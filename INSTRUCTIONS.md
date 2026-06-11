# Mapping Babel: Digital Tools for Area Studies Librarianship

**SALALM 71 — Politics of Place: Land and the State in Latin America, the Caribbean, and its Diasporas**  
University of Wisconsin–Madison Libraries · June 2026  
Brady Krien, Digital Humanities Coordinator, Digital Scholarship Hub

---

## Overview

In his short stories, "The Library of Babel" and "On Exactitude in Science," Jorge Luis Borges grapples with how to engage or even represent vast amounts of information. 

While area studies librarians don't have to contend with libraries that are the world or maps the size of the world, they often have to manage sizable collections that cover large geographies that have complex political, cultural, and publishing histories. 

Today we'll explore a few of the ways that library catalogs and data visualization can help provide visibility into the disposition and composition of collections. We'll develop visualizations that can help tell (part of) the story of a collection and which can answer some questions and invite more. 

---

## What You'll Need

- A free [Datawrapper](https://www.datawrapper.de) account (create one at datawrapper.de—this takes about two minutes with a Google or GitHub login)
- Internet browser (whichever you prefer)
- The data files in this repository (download individually or clone the repo)

No prior experience with data visualization or coding is required.

---

## The Dataset

The data in this repository is derived from UW's Latin American and Caribbean library catalog containing approximately 430,000 bibliographic records. It has been processed from the original MARC record files, (partially) cleaned, and aggregated for visualization. Don'y worry—you'll be working working with summary tables, not the full dataset raw catalog records.

The collection represents holdings in Spanish, Portuguese, English, French, and other languages, spanning publication dates from the 16th century to the present, across all major material types: books, serials, maps, music, film, and more.

### A note on the data

All datasets involve choices. This one is no exception. A few things worth knowing before you visualize:

#### Geographic coverage is partial.
About 51% of records carry structured geographic metadata that could be resolved to a specific country. The remaining 49% either lack geographic subject headings entirely or contain geographic references too granular or too far outside Latin America and the Caribbean to map. This limitation itself is interesting. The nature of the materials, combined with cataloging decisions and the inherent limitations of categorization mean that even questions such as "*where* is this item about?" may defy easy categorization. 
#### Country of publication data has known anomalies. 
MARC country codes are not ISO country codes, and miscoding occurs. Known issues have been corrected; others may remain.
#### Our goals are analysis and exploration, not evaluation.
 This is a large and complex collection that is imperfectly represented by the catalog which is itself imperfectly represented by the dataset with which we'll be working. This abstraction of an abstraction *is* useful but it's also inherently partial and has far more potential for provocation and interpretation than for any sort of evaluation of a collection. 

> **Invitation**: As we move throughout today's workshop I would encourage you to ask yourself:
> 1) What information is being obscured or elided by the visualization?
> 2) How might the data, analysis, or visualization that we do be useful in your own work? 
> 3) What stories do these visualizations tell and who might be a useful audience for them?

---

## Data Files

All files are CSV format and can be downloaded directly from this repository or loaded into Datawrapper.

| File | Description | Suggested visualization |
|---|---|---|
| `publication_by_country.csv` | Number of records by country of publication | map |
| `subject_by_country.csv` | Number of records by geographic subject coverage | map |
| `pub_vs_subject.csv` | Publication count, subject count, ratio, and interpretation by country | map (use `ratio_capped` or `interpretation` column) |
| `language_distribution.csv` | Record counts by language | bar chart |
| `publications_by_decade.csv` | Record counts by decade, 1800–present | line chart |
| `material_types_nonbook.csv` | Non-book material type breakdown | bar chart |
| `collection_enriched_v2.csv` | Publication counts normalized by population, land area, and years since independence | map or bar chart |
| `pivot_pub_country_by_decade.csv` | Record counts by publishing country and decade, wide format (1900–present; countries with 500+ records) | stacked bar chart |
| `pivot_material_by_decade.csv` | Record counts by material type and decade, wide format (1900–present; types with 100+ records) | stacked bar chart or grouped bar chart |
| `pivot_topic_country_by_decade.csv` | Record counts by geographic subject country and decade, wide format (1900–present; countries with 1,000+ subject records) | stacked bar chart |
---

## Workshop Activity

### Part 1—Guided (together)

We'll build two visualizations together as a group.

**Visualization 1: Language distribution bar chart**

1. Open [Datawrapper](https://www.datawrapper.de) and click **New Chart**
2. Select **Bar Chart**
3. Click **Upload data** and upload `language_distribution.csv`
4. Click **Proceed** through to **Visualize**
5. Under **Refine**, sort bars by value (largest to smallest)
6. Give your chart a title: *Languages Represented in Collection*
7. Click **Publish** to get a shareable link

*Discussion prompt: What does the language distribution tell you about this collection's relationship to the region? Is there anything that surprises you?*

**Visualization 2: Publication geography choropleth map**

> **Definition**: A **choropleth map** uses different colors to represent data. This type of map is commonly seen to represent election results where a political map of states in the US or of counties within a giving state are assigned colors to reflect their voting patterns. Learn more about map options in Datawrapper by visiting [this resource](https://www.datawrapper.de/maps).

1. Click **New Chart**, select **Map**, then **Choropleth map**
2. Choose **Latin America** as your base map
3. Upload `publication_by_country.csv`
4. Datawrapper will ask which column contains country names (`country_name`) and which contains values (`pub_count`)
5. Under **Visualize**, adjust the color scale — try both linear and diverging scales and notice how the story changes
6. Title your map: *Where does this collection come from?*
7. Publish and share

*Discussion prompt: What does this map make visible? What does it hide?*

---

### Part 2 — Explore on your own (30 minutes)

Using the remaining data files, build at least one more visualization of your choosing. Some starting questions:

- **What places does this collection talk about?** Load `subject_by_country.csv` and map it. How does this map differ from the publication geography map?
- **Where is the balance between how much a country publishes and how much a country is published *about*? Why does this matter?** Load `pub_vs_subject.csv` and map the `interpretation` column as a categorical variable. Which countries appear as "heavily written about" with little local publishing presence? What might explain that?
- **How has collecting changed over time?** Load `publications_by_decade.csv` and build a line chart. What patterns do you notice? Are there decades where acquisition appears to have accelerated or declined? What might have caused these shift (e.g., wars, economic downturns, etc.)
- **What does the collection look like when you normalize for population or size?** Load `collection_enriched_v2.csv` and map `pub_per_million_pop` or `pub_per_10k_km2`. Which countries look different on this map than on the raw count map? Do these even make sense as metrics?
- **How has the composition changed over time?** Load `pivot_material_by_decade.csv` and build a stacked bar chart of  materials by decade.

There are no right answers. The goal is to notice what different visualizations make legible and what they obscure.

---

## Datawrapper Quick Reference

### Loading data
- **Download CSV**: delect the dataset that you want to use and download it to your local computer
- **Upload CSV**: drag and drop or browse to your file

### Choropleth maps
- Datawrapper matches your country name column to its internal geography — check the **Match** tab to see which countries were recognized and which weren't
- Under **Visualize → Colors**, experiment with different scales: sequential (low to high), diverging (below/above a midpoint), categorical (for text columns like `interpretation`)
- Under **Annotate**, add a title, description, and data source note before publishing

### Charts
- Bar charts work best for categorical comparisons (language, material type)
- Line charts work best for time series (publications by decade)
- Under **Refine**, you can sort, filter, and color individual bars

### Publishing
- Every Datawrapper visualization gets a permanent public URL when you click **Publish** (you don't need to do this for tihs workshop)
- You can also embed visualizations in websites or export as PNG/SVG

---

## The Publisher to Subject Balance

One of the metrics in `pub_vs_subject.csv` and `collection_enriched_v2.csv` is the relationship between how many records in a collection were *published in* a given country versus how many records are *about* that country.

A high ratio means a country is written about more than the collection collects from it—the collection holds knowledge *about* that place, produced largely elsewhere. A low ratio means the collection primarily holds material produced there, with relatively less subject focus.

Neither is inherently good or bad. Some countries have thin publishing infrastructure; others are subjects of substantial international scholarship. The ratio is meaningful only in context—but it can prompt useful questions:

- Is the pattern you see for a particular country what you'd expect?
- How does your collection's ratio for a given country compare to peer institutions? How might specific institutional histories account for these differences?
- What would it take to shift the ratio—and would you want to?

The map that results from visualizing this balance is an argument. It encodes a information about the nature of publishing history in a country, the set of choices made over decades of acquisition, cataloging, and description, and relationships that may exist between bibliographers and publishers in a particular place. The goal of this workshop is not to evaluate those factors (indeed, the map wouldn't be nearly sufficient to draw firm conclusions) but to make some of the consequences of these factors visible and invite additional questions. 

---

## Going Further

### Tools
- **[Datawrapper](https://www.datawrapper.de)** — what we used today; excellent for choropleths, bar charts, and line charts; free public accounts available
- **[Felt](https://felt.com)** — browser-based mapping tool that supports custom tile layers, including historical maps from the David Rumsey Map Collection; good for narrative mapping
- **[ArcGIS StoryMaps](https://storymaps.arcgis.com)** — supports swipe comparisons between historical and modern maps, time-based visualizations, and rich narrative layering; free public accounts available with some feature limitations
- **[Palladio](https://hdlab.stanford.edu/palladio/)** — Stanford's browser-based humanities data visualization tool; good for network graphs and table-to-map workflows

### Getting your own catalog data
To do this analysis with your institution's collection, you'll need a MARC export of your Latin American holdings. Talk to your cataloging or systems librarian about:
- Exporting records filtered by subject heading, language, or call number range
- Requesting a CSV or JSON export if MARC binary is unfamiliar
- Understanding how your ILS (Alma, Sierra, Voyager, etc.) handles the export

The Python notebook used to process the raw MARC data for this workshop is available on request. It extracts geographic subject headings, language codes, publication dates, and country of publication from MARC records and aggregates them into files like the ones in this repository. The same workflow can be applied to any library's catalog export.

---

## About This Workshop

This workshop was developed for SALALM 71 by Brady Krien, Digital Humanities Coordinator at the Digital Scholarship Hub, UW–Madison Libraries. The Digital Scholarship Hub supports digital scholarship methods — including data analysis, text mining, network analysis, and digital mapping — for faculty, graduate students, and library colleagues across the humanities and humanistic social sciences.

**Digital Scholarship Hub:** [https://www.library.wisc.edu/digital-scholarship-hub/](https://www.library.wisc.edu/digital-scholarship-hub/)

Questions about this workshop or the underlying data? Contact Brady Krien at [brady.krien@wisc.edu](mailto:brady.krien@wisc.edu).

**AI Statement**: This workshop's data pipeline was developed utilizing Anthropic's Claude (Sonnect4.6). Claude contributed to the Python code for MARC record parsing, geographic place name resolution, country code verification, and dataset aggregation, as well as the documentation in this repository. The intellectual framing, analytical decisions, and all final judgments about the data were made by the Brady Krien.

---

*Data derived from UW–Madison Libraries catalog holdings. Processed June 2026.*
