# PatSnap Pharma Intelligence

**PatSnap Pharma Intelligence** is a Model Context Protocol (MCP) server that equips AI agents with comprehensive pharmaceutical intelligence — covering drugs, targets, diseases, patents, clinical trials, deals, papers, FDA labels, epidemiology, financial reports, news, and translational medicine. Built on PatSnap's global life sciences platform with over 200M+ records, it enables structured search, semantic vector search, and entity retrieval across the full drug development lifecycle.

## Quick Links
- [PatSnap Life Science Home](https://eureka.patsnap.com/ls-landing)
- [PatSnap Developer Portal](https://open.patsnap.com)
- [PatSnap Biology Modality MCP](https://open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097)
  
## Setup

### 1. Get an API Key
Log in to [PatSnap Developer Platform](https://open.patsnap.com), go to **API Keys**, and create a new key (format: `sk-xxxxxxxxxxxx`).

### 2. Connect the MCP Server
Run the following command in your terminal (requires [Claude Code](https://claude.ai) or any MCP-compatible client):

```bash
claude mcp add --transport http pharma_intelligence \
  "https://connect.patsnap.com/096456/Logic-mcp?apiKey=$PATSNAP_API_KEY"
```

Set your API key as an environment variable:

```bash
export PATSNAP_API_KEY=sk-your-key-here
```

> **Other clients?** Visit the [Pharma Intelligence page on PatSnap Marketplace](https://open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097) and select your agent (Cursor, API, etc.) from the bottom‑right corner to get the appropriate configuration snippet.

### 3. Verify
In Claude Code, type `/mcp` and confirm `pharma_intelligence` shows **Connected**.

## Available Tools

> **Note for AI Agents:** This server provides 28 tools organized into three groups: Entity Search & Fetch (structured queries with pagination), Vector Search (semantic natural-language queries), and Special Tools (normalization and web search). Prefer `ls_ner_nor_normalize` to extract structured entities from user input before passing them to search tools. Avoid over-generalizing meta-words in vector search queries — use only biology, chemistry, and pharmaceutical-related terms.

---

### Entity Search & Fetch

These tools use structured field filters to retrieve domain-specific records. Each search tool has a corresponding fetch tool that retrieves full detail records by ID.

#### 1. `ls_drug_search`
- **Purpose**: Search drug assets by name, target, disease, organization, development phase, or milestone date. Ideal for structured pipeline filtering.
- **Parameters**:
  - `drug` (array of strings, optional): Drug name list to locate specific assets.
  - `target` (array of strings, optional): Target name list for target-centric drug discovery queries.
  - `disease` (array of strings, optional): In-development disease name list for pipeline filtering.
  - `organization` (array of strings, optional): R&D organization name list for sponsor/originator/developer filtering.
  - `mechanism_action` (array of strings, optional): Mechanism of action name list.
  - `drug_type` (array of strings, optional): Drug type filter.
  - `atc_code` (array of strings, optional): ATC code filter for therapy-area or class-based retrieval.
  - `action_type` (array of strings, optional): Action type filter for activity mode.
  - `country` (array of strings, optional): Country or region code list.
  - `highest_phase` (array of strings, optional): Global highest development status filter. Allowed values include `"discovery"`, `"preclinical"`, `"phase_1"`, `"phase_2"`, `"phase_3"`, `"approved"`, `"phase_4"`, `"discontinued"`, `"suspended"`, `"withdrawn"`, and others.
  - `dev_status` (array of strings, optional): Current development status filter.
  - `dev_status_org_is_startups` (boolean, optional): Whether the associated organization is a startup.
  - `exist_deal` (boolean, optional): Whether the drug has any related deal records.
  - `modification` (array of strings, optional): Chemical modification ID filter.
  - `org_type` (array of strings, optional): Organization type filter. Allowed values: `"company"`, `"university_institution"`, `"other"`.
  - `phase1_date_from` / `phase1_date_to` (string, optional): First Phase 1 milestone date range. Format: `YYYY-MM-DD`.
  - `phase2_date_from` / `phase2_date_to` (string, optional): First Phase 2 milestone date range.
  - `phase3_date_from` / `phase3_date_to` (string, optional): First Phase 3 milestone date range.
  - `ind_application_date_from` / `ind_application_date_to` (string, optional): First IND filing date range.
  - `nda_bla_date_from` / `nda_bla_date_to` (string, optional): First NDA/BLA filing date range.
  - `nda_approval_date_from` / `nda_approval_date_to` (string, optional): First approval date range.
  - `highest_phase_date_from` / `highest_phase_date_to` (string, optional): Highest-phase milestone date range.
  - `key_word` (array of strings, optional): Free-text keyword for broad matching. Use only if specific fields return insufficient results.
  - `offset` (integer, optional): Pagination offset.
  - `limit` (integer, optional): Page size.
- **Returns**: JSON object with `total_hits` (integer) and `results` (array of drug records).
- **API**: `POST /api/ls/drug/search`
- **Usage**: Use for structured pipeline queries like "Phase 3 PD-1 drugs in China" or "approved drugs from a specific company". For full records, call `ls_drug_fetch` with returned IDs.

#### 2. `ls_drug_fetch`
- **Purpose**: Batch fetch full detail records by drug IDs or drug names.
- **Parameters**:
  - `drug_ids` (array of strings, optional): Drug ID list in UUID format.
  - `drug` (array of strings, optional): Drug name list. When provided, names are resolved to IDs before fetching.
- **Returns**: JSON object with full detail records for the requested drugs.
- **API**: `POST /api/ls/drug/fetch`
- **Usage**: Call after `ls_drug_search` with the IDs from search results to get complete information.

#### 3. `ls_patent_search`
- **Purpose**: Search patents by drug, target, disease, applicant organization, patent category, or publication date. Suitable for structured patent landscaping.
- **Parameters**:
  - `drug` (array of strings, optional): Drug name list for therapy-associated patent retrieval.
  - `target` (array of strings, optional): Target name list for target-centered patent landscaping.
  - `disease` (array of strings, optional): Disease name list for disease-area patent retrieval.
  - `organization` (array of strings, optional): Applicant or organization name list.
  - `inventors` (array of strings, optional): Inventor name list.
  - `patent_number` (string, optional): Patent number filter, matched against both `PN` and `APNO`.
  - `country` (array of strings, optional): Country or region code list.
  - `patent_core_type` (array of strings, optional): Patent classification filter. Allowed values include `"product_compound"`, `"sequence"`, `"drug_combination"`, `"formulation"`, `"process"`, `"new_use"`, and others.
  - `patent_technology` (array of strings, optional): Patent technology type. Allowed values include `"Antibody drug conjugate (ADC)"`, `"Monoclonal antibody (mAb)"`, `"CRISPR/Cas"`, and others.
  - `drug_type` (array of strings, optional): Drug type filter.
  - `legal_status` (array of strings, optional): Legal status filter. Allowed values: `"inactive"`, `"active"`, `"pending"`, `"pct_designated_stage"`, `"pct_designated_stage_expired"`.
  - `applicant_type` (array of strings, optional): Applicant type filter. Allowed values: `"academy"`, `"company"`, `"government"`, `"person"`, `"hospital"`, `"bank"`.
  - `publication_date_from` / `publication_date_to` (string, optional): Publication date range. Format: `YYYY-MM-DD`.
  - `application_date_from` / `application_date_to` (string, optional): Application date range.
  - `expiry_date_from` / `expiry_date_to` (string, optional): Expiry date range.
  - `key_word` (array of strings, optional): Free-text keyword for broad matching.
  - `offset` (integer, optional): Pagination offset.
  - `limit` (integer, optional): Page size.
- **Returns**: JSON object with `total_hits` (integer) and `results` (array of patent records).
- **API**: `POST /api/ls/patent/search`
- **Usage**: Use for queries like "ADC patents in CN after 2020" or "PD-1 related patents from Merck". For full records, call `ls_patent_fetch`.

#### 4. `ls_patent_fetch`
- **Purpose**: Batch fetch full detail records by patent IDs or patent numbers.
- **Parameters**:
  - `patent_ids` (array of strings, optional): Patent ID list in UUID format.
  - `pn` (array of strings, optional): Patent number list. Numbers are resolved to IDs via NER-NOR before fetching.
- **Returns**: JSON object with full detail records for the requested patents.
- **API**: `POST /api/ls/patent/fetch`
- **Usage**: Call after `ls_patent_search` with returned IDs or patent numbers.

#### 5. `ls_clinical_trial_search`
- **Purpose**: Search registered clinical trials by study drug, control drug, target, disease, sponsor, phase, or geography. Suitable for structured trial filtering.
- **Parameters**:
  - `drug` (array of strings, optional): Main study drug name list.
  - `control_drug` (array of strings, optional): Control drug name list for comparator-arm filtering.
  - `target` (array of strings, optional): Target name list for mechanism-focused trial retrieval.
  - `disease` (array of strings, optional): Disease name list for trial population or indication context.
  - `organization` (array of strings, optional): Sponsor or collaborator organization name list.
  - `mechanism_action` (array of strings, optional): Mechanism of action name list.
  - `drug_type` (array of strings, optional): Drug type filter.
  - `phase` (array of strings, optional): Clinical phase filter. Common values: `"early_phase_1"`, `"phase_1"`, `"phase_1_2"`, `"phase_2"`, `"phase_2_3"`, `"phase_3"`, `"phase_4"`, `"not_applicable"`.
  - `study_status` (array of strings, optional): Trial status filter. Allowed values: `"not_yet_recruiting"`, `"recruiting"`, `"enrolling_by_invitation"`, `"active_not_recruiting"`, `"suspended"`, `"terminated"`, `"completed"`, `"withdrawn"`.
  - `therapeutic_area` (array of strings, optional): Therapeutic area name list (e.g., `"neoplasms"`, `"cardiovascular_diseases"`).
  - `country` (array of strings, optional): Country or region code list.
  - `route_of_administration` (array of strings, optional): Route of administration filter.
  - `dosage_form` (array of strings, optional): Dosage form filter.
  - `register_number` (string, optional): Trial registration number, such as an NCT number.
  - `study_identifier` (string, optional): Sponsor study code or internal identifier.
  - `brief_title` (string, optional): Clinical trial title or brief public title.
  - `enrollment_from` / `enrollment_to` (integer, optional): Enrollment size range.
  - `start_date_from` / `start_date_to` (string, optional): Trial start date range. Format: `YYYY-MM-DD`.
  - `study_first_posted_date_from` / `study_first_posted_date_to` (string, optional): First posted date range.
  - `key_word` (array of strings, optional): Free-text keyword for broad matching.
  - `offset` (integer, optional): Pagination offset.
  - `limit` (integer, optional): Page size.
- **Returns**: JSON object with `total_hits` (integer) and `results` (array of clinical trial records).
- **API**: `POST /api/ls/clinical-trial/search`
- **Usage**: Use for queries like "Phase 2 EGFR trials in US" or "PD-1 studies sponsored by Merck". For full records, call `ls_clinical_trial_fetch`.

#### 6. `ls_clinical_trial_fetch`
- **Purpose**: Batch fetch full detail records by clinical trial IDs or registration numbers.
- **Parameters**:
  - `trial_ids` (array of strings, optional): Clinical trial ID list in UUID format.
  - `registration_number` (array of strings, optional): Registration number list. Numbers are resolved to IDs via NER-NOR before fetching.
- **Returns**: JSON object with full detail records for the requested trials.
- **API**: `POST /api/ls/clinical-trial/fetch`
- **Usage**: Call after `ls_clinical_trial_search` with returned trial IDs or registration numbers.

#### 7. `ls_clinical_trial_result_search`
- **Purpose**: Search published or indexed clinical trial results by drug, target, disease, sponsor, phase, or evaluation outcome. Suitable for result-centric queries.
- **Parameters**:
  - `drug` (array of strings, optional): Main study drug name list for the treated cohort.
  - `control_drug` (array of strings, optional): Control drug name list for comparator-arm result filtering.
  - `target` (array of strings, optional): Target name list for mechanism-centered result retrieval.
  - `disease` (array of strings, optional): Disease name list for the trial population or indication.
  - `organization` (array of strings, optional): Sponsor or collaborator organization name list.
  - `mechanism_action` (array of strings, optional): Mechanism of action name list.
  - `drug_type` (array of strings, optional): Drug type filter.
  - `phase` (array of strings, optional): Clinical phase filter.
  - `therapy_type` (array of strings, optional): Therapy-line or treatment-pattern filter. Allowed values: `"first_line"`, `"second_line"`, `"third_line"`, `"last_line"`, `"adjuvant"`, `"neoadjuvant"`, `"maintenance"`, `"consolidation"`, `"add_on"`, `"induction"`.
  - `general_evaluation` (array of strings, optional): Overall trial evaluation filter. Allowed values: `"superiority"`, `"positive"`, `"non_inferiority"`, `"similar"`, `"non_superiority"`, `"negative"`.
  - `therapeutic_area` (array of strings, optional): Therapeutic area name list.
  - `register_number` (string, optional): Registration number.
  - `study_code` (string, optional): Study code or sponsor trial identifier.
  - `overall_enrollment_from` / `overall_enrollment_to` (integer, optional): Evaluated population size range.
  - `published_date_from` / `published_date_to` (string, optional): Result publication date range. Format: `YYYY-MM-DD`.
  - `key_word` (array of strings, optional): Free-text keyword for broad matching.
  - `offset` (integer, optional): Pagination offset.
  - `limit` (integer, optional): Page size.
- **Returns**: JSON object with `total_hits` (integer) and `results` (array of clinical trial result records).
- **API**: `POST /api/ls/clinical-trial-result/search`
- **Usage**: Use for queries like "Phase 3 PD-1 trial results in melanoma" or "positive EGFR trial readouts after 2022". For full records, call `ls_clinical_trial_result_fetch`.

#### 8. `ls_clinical_trial_result_fetch`
- **Purpose**: Batch fetch full detail records by clinical trial result IDs.
- **Parameters**:
  - `result_ids` (array of strings, required): Clinical trial result ID list in UUID format.
- **Returns**: JSON object with full detail records for the requested trial results.
- **API**: `POST /api/ls/clinical-trial-result/fetch`
- **Usage**: Call after `ls_clinical_trial_result_search` with returned result IDs.

#### 9. `ls_paper_search`
- **Purpose**: Search academic papers by drug, target, disease, organization, journal, author, or publication year. Effective for evidence-finding queries.
- **Parameters**:
  - `drug` (array of strings, optional): Drug name list for evidence gathering around a specific therapy.
  - `target` (array of strings, optional): Target name list for target-centric literature retrieval.
  - `disease` (array of strings, optional): Disease name list to constrain therapeutic context.
  - `organization` (array of strings, optional): Organization name list matching author affiliations.
  - `journal` (array of strings, optional): Journal name list.
  - `authors` (array of strings, optional): Author name list.
  - `drug_type` (array of strings, optional): Drug type filter.
  - `year_from` / `year_to` (string, optional): Publication date boundaries. Format: `YYYY-MM-DD`.
  - `key_word` (array of strings, optional): Free-text keyword for broad matching.
  - `offset` (integer, optional): Pagination offset.
  - `limit` (integer, optional): Page size.
- **Returns**: JSON object with `total_hits` (integer) and `results` (array of paper records).
- **API**: `POST /api/ls/paper/search`
- **Usage**: Use for queries like "recent Nature Medicine papers about KRAS inhibitors" or "papers from Dana-Farber on PD-1". For full records, call `ls_paper_fetch`.

#### 10. `ls_paper_fetch`
- **Purpose**: Batch fetch full detail records by paper IDs.
- **Parameters**:
  - `paper_ids` (array of strings, required): Paper ID list in UUID format.
- **Returns**: JSON object with full detail records for the requested papers.
- **API**: `POST /api/ls/paper/fetch`
- **Usage**: Call after `ls_paper_search` with returned paper IDs.

#### 11. `ls_drug_deal_search`
- **Purpose**: Search licensing, collaboration, acquisition, or option deals related to a drug, target, disease, or company. Suitable for business development queries.
- **Parameters**:
  - `drug` (array of strings, optional): Drug name list for transactions related to a specific asset.
  - `target` (array of strings, optional): Target name list for target-specific BD searches.
  - `deal_disease` (array of strings, optional): Deal indication name list.
  - `drug_disease` (array of strings, optional): Drug indication name list for the asset itself.
  - `licensor` (array of strings, optional): Licensor organization name list.
  - `licensee` (array of strings, optional): Licensee organization name list.
  - `mechanism_action` (array of strings, optional): Mechanism of action name list.
  - `drug_type` (array of strings, optional): Drug type filter.
  - `phase` (array of strings, optional): Highest development phase at deal time.
  - `deal_type` (array of strings, optional): Deal type filter. Allowed values: `"collaboration"`, `"option"`, `"investment"`, `"asset_acquisition"`, `"merger_and_acquisition"`, `"license"`.
  - `country` (array of strings, optional): Rights territory code list.
  - `deal_date_from` / `deal_date_to` (string, optional): Deal date range. Format: `YYYY-MM-DD`.
  - `key_word` (array of strings, optional): Free-text keyword for broad matching.
  - `offset` (integer, optional): Pagination offset.
  - `limit` (integer, optional): Page size.
- **Returns**: JSON object with `total_hits` (integer) and `results` (array of deal records).
- **API**: `POST /api/ls/drug-deal/search`
- **Usage**: Use for queries like "ADC licensing deals in US after 2021" or "Phase 2 KRAS deals involving Novartis". For full records, call `ls_drug_deal_fetch`.

#### 12. `ls_drug_deal_fetch`
- **Purpose**: Batch fetch full detail records by drug deal IDs.
- **Parameters**:
  - `drug_deal_ids` (array of strings, required): Drug deal ID list in UUID format.
- **Returns**: JSON object with full detail records for the requested deals.
- **API**: `POST /api/ls/drug-deal/fetch`
- **Usage**: Call after `ls_drug_deal_search` with returned deal IDs.

#### 13. `ls_disease_fetch`
- **Purpose**: Batch fetch full detail records by disease IDs or disease names.
- **Parameters**:
  - `disease_ids` (array of strings, optional): Disease ID list in UUID format.
  - `disease` (array of strings, optional): Disease name list. Names are resolved to IDs before fetching.
- **Returns**: JSON object with full detail records for the requested diseases.
- **API**: `POST /api/ls/disease/fetch`
- **Usage**: Use when you need complete disease profiles including associated targets, drugs, and clinical trials.

#### 14. `ls_target_fetch`
- **Purpose**: Batch fetch full detail records by target IDs or target names.
- **Parameters**:
  - `target_ids` (array of strings, optional): Target ID list in UUID format.
  - `target` (array of strings, optional): Target name list. Names are resolved to IDs before fetching.
- **Returns**: JSON object with full detail records for the requested targets.
- **API**: `POST /api/ls/target/fetch`
- **Usage**: Use when you need complete target profiles including associated drugs, diseases, and mechanisms.

#### 15. `ls_organization_fetch`
- **Purpose**: Batch fetch full detail records by organization IDs or organization names.
- **Parameters**:
  - `organization_ids` (array of strings, optional): Organization ID list in UUID format.
  - `organization` (array of strings, optional): Organization name list. Names are resolved to IDs before fetching.
- **Returns**: JSON object with full detail records for the requested organizations.
- **API**: `POST /api/ls/organization/fetch`
- **Usage**: Use to retrieve complete organization profiles including pipeline, partnerships, and publication records.

#### 16. `ls_translational_medicine_search`
- **Purpose**: Search translational medicine records by drug, target, disease, sponsor, journal, or translation stage. Effective for structured follow-up queries after entity extraction.
- **Parameters**:
  - `drug` (array of strings, optional): Drug name list to narrow translational studies to a specific therapy.
  - `target` (array of strings, optional): Target name list for biology- or mechanism-oriented queries.
  - `disease` (array of strings, optional): Disease name list to constrain clinical or biological context.
  - `organization` (array of strings, optional): Organization name list for research institution or sponsor.
  - `mechanism_action` (array of strings, optional): Mechanism of action name list.
  - `drug_type` (array of strings, optional): Drug type filter.
  - `journal` (array of strings, optional): Journal name list.
  - `subject` (array of strings, optional): Research subject filter. Allowed values: `"epidemiology"`, `"pathogenesis"`, `"target"`, `"biomarker"`, `"structural_biology"`, `"discovery_preclinical"`, `"phase_1_clinical"`, `"phase_1_2_clinical"`, `"phase_2_clinical"`, `"phase_2_3_clinical"`, `"phase_3_clinical"`, `"post_marketing_study"`, `"real_world_research"`.
  - `translation_stage` (array of strings, optional): Translation stage filter. Allowed values: `"t0"`, `"t1"`, `"t2"`, `"t3"`.
  - `published_date_from` / `published_date_to` (string, optional): Publication date range. Format: `YYYY-MM-DD`.
  - `key_word` (array of strings, optional): Free-text keyword for broad matching.
  - `offset` (integer, optional): Pagination offset.
  - `limit` (integer, optional): Page size.
- **Returns**: JSON object with `total_hits` (integer) and `results` (array of translational medicine records).
- **API**: `POST /api/ls/translational-medicine/search`
- **Usage**: Use for narrowing results to a specific disease area, sponsor, or publication window. For full records, call `ls_translational_medicine_fetch`.

#### 17. `ls_translational_medicine_fetch`
- **Purpose**: Batch fetch full detail records by translational medicine IDs.
- **Parameters**:
  - `translational_medicine_ids` (array of strings, required): Translational medicine ID list in UUID format.
- **Returns**: JSON object with full detail records for the requested translational medicine entries.
- **API**: `POST /api/ls/translational-medicine/fetch`
- **Usage**: Call after `ls_translational_medicine_search` with returned IDs.

---

### Vector Search

These tools use semantic similarity to search domain-specific content. All vector search tools share a common interface: `query` (required natural-language string), `top_k` (optional integer, default 20), and `lang` (required, `"CN"` or `"EN"`). Queries must use only biology, chemistry, and pharmaceutical-related terms — avoid meta-words like "literature", "paper", "review", "report", "patent", or "drug development".

#### 18. `ls_patent_vector_search`
- **Purpose**: Search patents with semantic similarity. Useful for complex natural-language queries that cannot be expressed through structured field filters alone.
- **Parameters**: `query` (string, required), `top_k` (integer, optional, default 20), `lang` (string, required, `"CN"` or `"EN"`).
- **Returns**: JSON object with relevant text chunks from matching patents.
- **API**: `POST /api/ls/patent/vector-search`
- **Usage**: Use when the user's query is conceptual rather than structured.

#### 19. `ls_paper_vector_search`
- **Purpose**: Search academic papers with semantic similarity.
- **Parameters**: `query` (string, required), `top_k` (integer, optional, default 20), `lang` (string, required).
- **Returns**: JSON object with relevant text chunks from matching papers.
- **API**: `POST /api/ls/paper/vector-search`
- **Usage**: Use for conceptual queries about mechanisms, evidence synthesis, or clinical findings.

#### 20. `ls_clinical_trial_vector_search`
- **Purpose**: Search clinical trials with semantic similarity.
- **Parameters**: `query` (string, required), `top_k` (integer, optional, default 20), `lang` (string, required).
- **Returns**: JSON object with relevant text chunks from matching clinical trials.
- **API**: `POST /api/ls/clinical-trial/vector-search`
- **Usage**: Use for complex trial design or population queries.

#### 21. `ls_clinical_guideline_vector_search`
- **Purpose**: Search clinical guidelines with semantic similarity.
- **Parameters**: `query` (string, required), `top_k` (integer, optional, default 20), `lang` (string, required).
- **Returns**: JSON object with relevant text chunks from matching clinical guidelines.
- **API**: `POST /api/ls/clinical-guideline/vector-search`
- **Usage**: Use for treatment protocol, standard-of-care, or guideline recommendation queries.

#### 22. `ls_fda_label_vector_search`
- **Purpose**: Search FDA drug labels with semantic similarity.
- **Parameters**: `query` (string, required), `top_k` (integer, optional, default 20), `lang` (string, required).
- **Returns**: JSON object with relevant text chunks from matching FDA labels.
- **API**: `POST /api/ls/fda-label/vector-search`
- **Usage**: Use for approved indication, dosing, safety, or regulatory queries.

#### 23. `ls_epidemiology_vector_search`
- **Purpose**: Search epidemiology data with semantic similarity.
- **Parameters**: `query` (string, required), `top_k` (integer, optional, default 20), `lang` (string, required).
- **Returns**: JSON object with relevant text chunks from matching epidemiology content.
- **API**: `POST /api/ls/epidemiology/vector-search`
- **Usage**: Use for disease prevalence, incidence, or population health queries.

#### 24. `ls_news_vector_search`
- **Purpose**: Search news content with semantic similarity.
- **Parameters**: `query` (string, required), `top_k` (integer, optional, default 20), `lang` (string, required).
- **Returns**: JSON object with relevant text chunks from matching news articles.
- **API**: `POST /api/ls/news/vector-search`
- **Usage**: Use for recent developments, market events, or competitor news.

#### 25. `ls_financial_report_vector_search`
- **Purpose**: Search financial reports and prospectuses with semantic similarity.
- **Parameters**: `query` (string, required), `top_k` (integer, optional, default 20), `lang` (string, required).
- **Returns**: JSON object with relevant text chunks from matching financial reports.
- **API**: `POST /api/ls/financial-report/vector-search`
- **Usage**: Use for company revenue, R&D spending, or market forecast queries.

---

### Special Tools

#### 26. `ls_news_fetch`
- **Purpose**: Batch fetch full detail records by news IDs.
- **Parameters**:
  - `news_ids` (array of strings, required): News ID list in UUID format.
- **Returns**: JSON object with full detail records for the requested news articles.
- **API**: `POST /api/ls/news/fetch`
- **Usage**: Call after `ls_news_vector_search` with returned IDs.

#### 27. `ls_web_search`
- **Purpose**: Search the web for current information on a specific topic. Returns a list of relevant web results.
- **Parameters**:
  - `query` (string, required): Search query string.
- **Returns**: JSON object with `results` (array of web search result records).
- **API**: `POST /api/ls/web/search`
- **Usage**: Use for accessing information beyond PatSnap's curated databases. Prefer domain-specific search tools (drug, patent, paper, clinical trial) for structured queries.

#### 28. `ls_ner_nor_normalize`
- **Purpose**: Identify and normalize entities (targets, drugs, diseases, companies, drug types, mechanisms, action types, patent numbers, clinical trial numbers) from user input text. Runs NER-NOR API and LLM keyword extraction in parallel, then merges and deduplicates results via autocomplete.
- **Parameters**:
  - `user_input` (string, required): The user's raw query text. Must not be modified or preprocessed before passing.
- **Returns**: JSON object with normalized entity lists organized by type.
- **API**: `POST /api/ls/ner-nor/normalize`
- **Usage**: Always use this tool first to extract structured entities from the user's natural-language input, then pass the normalized entities to the appropriate domain search tools.

## 💡 **Need help?**
Visit: [PatSnap Life Science](https://eureka.patsnap.com/ls-landing) 
or  [PatSnap Dev Portal](https://open.patsnap.com/devportal)

---

## Integration with PatSnap Skills
This server powers the core pharmaceutical intelligence layer for the following PatSnap Skills (Claude Code agents):
- **biomarker-investigation** — uses disease, target, and clinical trial search to contextualize biomarker findings.
- **company-profiling** — uses organization, drug, patent, and deal search to build comprehensive company profiles.
- **disease-investigation** — uses disease, target, drug, clinical trial, and paper search to characterize disease landscapes.
- **precision-oncology** — uses target, drug, clinical trial, and patent search to evaluate oncology precision therapies.
- **pharmaceuticals-exploration** — uses drug, patent, clinical trial, and deal search to assess pharmaceutical assets.
- **target-intelligence** — uses target, drug, disease, and paper search to evaluate therapeutic targets.

Each Skill automatically invokes the appropriate tools from this server when performing its analyses. You can install the Skills from the [PatSnap Skills Library](https://github.com/patsnap/skills/tree/main/life-sciences). 
Or, if you use openclaw:
```bash
openclaw skills install SKILL_NAME
```

## License
MIT
