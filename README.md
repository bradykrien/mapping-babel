# Mapping Babel: Digital Tools for Area Studies Librarianship
Repository for workshop for the SALALM71 Conference held at UW–Madison in June 2026. 

The Instructions file provides guidance for completing the activity. 

The data files contain the data with which we'll be working during this session. A brief explanation of the data files is below:

`publication_by_country.csv`  
Two columns: country_name and pub_count. Each row represents a country or territory in Latin America and the Caribbean, with a count of how many records in the collection were published there. Country of publication is derived from the MARC 008 fixed field, which carries a coded country of publication for every record. Only countries and territories within Latin America and the Caribbean are included; records published in the United States, Spain, the United Kingdom, and other locations outside the region are excluded. Use this file to ask: where does this collection come from?

`subject_by_country.csv`  
Two columns: country_name and subject_count. Each row represents a country or territory, with a count of how many records in the collection carry geographic subject headings referencing that place. Geographic subject information was drawn from two MARC sources: the 651 geographic subject heading field, and geographic subdivisions ($z subfields) embedded within 650 topical subject headings. A single record can contribute to multiple countries if it carries subject headings for more than one place. Use this file to ask: what places does this collection talk about?

`pub_vs_subject.csv`  
Seven columns: country_name, pub_count, subject_count, ratio, interpretation, log_ratio, and ratio_capped. This file combines the publication and subject geography data into a single table and adds two derived measures. The ratio column expresses the relationship between subject coverage and publishing presence for each country — a high ratio means the collection talks about a place more than it collects from it; a low ratio means the opposite. The interpretation column assigns a plain-language label to each country: Publishing-heavy, Balanced, Heavily written about, or No local publishing. The ratio_capped column limits extreme values to a maximum of 10 for cleaner visualization; the log_ratio column applies a logarithmic transformation for use in choropleth maps where extreme outliers would otherwise dominate the color scale. Use this file to ask: where is the gap between voice and representation?

`language_distribution.csv`  
Two columns: language and count. Each row represents a language, with a count of records cataloged in that language. Language is derived from the MARC 008 fixed field positions 35–37, which carry a three-letter language code for every record. Codes have been mapped to full language names. Use this file to ask: what languages does this collection speak?

`publications_by_decade.csv`  
Two columns: decade and count. Each row represents a decade from 1800 to 2020, with a count of records whose publication date falls within that decade. Publication date is derived from the MARC 008 fixed field positions 7–10. Dates coded as unknown or open-ended (e.g., currently publishing serials) are excluded. The 2020s decade is incomplete and will appear lower than preceding decades as a result. Use this file to ask: how has this collection grown over time, and are there periods of acceleration or decline?

`collection_enriched_v2.csv`  
Thirteen columns combining publication counts with contextual data about each country or territory: country_name, pub_count, population, land_area_km2, independence_year, is_territory, territory_note, years_independent, pub_per_million_pop, pub_per_10k_km2, and pub_per_year_independent. Population figures are 2026 estimates from Worldometer, sourced from UN World Population Prospects. Land area figures are from Worldometer. Independence years are drawn from historical sources and verified against multiple references. The seven territories in the dataset (Puerto Rico, Guadeloupe, Martinique, French Guiana, United States Virgin Islands, Cayman Islands, British Virgin Islands) are flagged in the is_territory column; their independence_year and pub_per_year_independent values are set to 0 as the concept of independence does not apply. Use this file to ask: what does the collection look like when you control for country size, population, or how long a nation has had the conditions for independent publishing?

`pivot_pub_country_by_decade.csv`  
Wide-format table with one row per decade (1900–2020) and one column per major publishing country. Each cell contains the number of records published in that country during that decade. Countries with fewer than 500 total records across all decades are excluded for readability. This file is designed for use as a stacked bar chart in Datawrapper, where the x-axis is the decade and each country's column becomes one segment of the stack. Use this file to ask: how has the geographic origin of the collection's acquisitions shifted over time?

`pivot_material_by_decade.csv`  
Wide-format table with one row per decade (1900–2020) and one column per material type. Each cell contains the number of records of that material type from that decade. Material types with fewer than 100 total records are excluded. This file is designed for use as a stacked bar chart or grouped bar chart in Datawrapper. Use this file to ask: has the format composition of the collection changed over time — for instance, has digital and audiovisual material grown relative to print?

`pivot_topic_country_by_decade.csv`  
Wide-format table with one row per decade (1900–2020) and one column per country that appears as a geographic subject. Each cell contains the number of records that carry subject headings referencing that country during that decade. Because a single record can reference multiple countries, counts across columns are not mutually exclusive. Countries with fewer than 1,000 total subject records are excluded for readability. Use this file to ask: has scholarly and collecting attention to different countries in the region shifted over time — and do you see any countries whose subject presence rises or falls in ways that reflect historical events?
