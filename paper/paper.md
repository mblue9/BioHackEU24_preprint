---
title: 'BioHackEU24 report: Integrating Bioconductor packages with the ELIXIR Research Software Ecosystem using EDAM'
title_short: 'BioHackEU24 #27: Integrating Bioconductor with ELIXIR RSEc'
tags:
  - bioinformatics
  - ontology
  - biohackeu24
authors:
  - name: Claire Rioualen
    orcid: "0000-0002-7684-8679"
    affiliation: 1
  - name: Vincent J Carey
    orcid: "0000-0003-4046-0063"
    affiliation: 2   
  - name: Matúš Kalaš
    orcid: "0000-0002-1509-4981"
    affiliation: 3
  - name: Sebastian Lobentanzer
    orcid: "0000-0003-3399-6695"
    affiliation: 4
  - name: Hervé Ménager
    orcid: "0000-0002-7552-1009"
    affiliation: 1, 5
  - name: Egon Willighagen
    orcid: 0000-0001-7542-0286
    affiliation: 6
  - name: firstName lastName
    orcid: "0000-0000-0000-0000"
    affiliation: 7
  - name: Maria A Doyle
    orcid: "0000-0003-4847-8436"
    affiliation: n  
affiliations:
  - name: IFB-core, Institut Français de Bioinformatique (IFB), CNRS, INSERM, INRAE, CEA, 91057 Evry, France
    index: 1
  - name: Channing Division of Network Medicine, Mass General Brigham, Harvard Medical School, Boston MA, 02115 USA
    index: 2
  - name: ELIXIR Norway, and Department of Informatics, University of Bergen, Norway
    index: 3
  - name: Heidelberg University, Faculty of Medicine and Heidelberg University Hospital, Institute for Computational Biomedicine, Heidelberg, Germany
    index: 4
  - name: Institut Pasteur, Université Paris Cité, Bioinformatics and Biostatistics Hub, 75015, Paris, France
    index: 5
  - name: Dept of Translational Genomics, NUTRIM, FHML, Maastricht University, Maastricht, Netherlands
    index: 6
  - name: xxx
    index: 7
  - name: Limerick Digital Cancer Research Centre, Health Research Institute, School of Medicine, University of Limerick, V94 T9PX, Ireland
    index: n
date: 8 November 2024
cito-bibliography: paper.bib
event: BH24EU
biohackathon_name: "BioHackathon Europe 2024"
biohackathon_url:   "https://biohackathon-europe.org/"
biohackathon_location: "Barcelona, Spain, 2024"
group: Project 27
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/mblue9/BioHackEU24_preprint
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: Claire Rioualen \emph{et al.}
---

# Abstract

This project seeks to enhance the ELIXIR Research Software Ecosystem (RSEc) by increasing the findability, accessibility, interoperability, and reusability (FAIR principles) of Bioconductor’s extensive collection of over 2,000 bioinformatics packages. By aligning Bioconductor metadata with the EDAM ontology and integrating detailed package descriptions into the bio.tools registry, this project will significantly improve the search, discovery, and usability of genomic data analysis tools within the R environment. The short-term goals involve mapping EDAM terms to Bioconductor’s biocViews taxonomy, developing a gold standard of manually annotated packages, and assessing tools for automated EDAM term suggestions. Long-term, we aim to expand EDAM coverage to the full Bioconductor ecosystem, phase out biocViews, and implement an automated synchronisation mechanism with the bio.tools registry. This initiative also fosters a collaborative pathway between the Bioconductor and ELIXIR communities, promoting sustainable and scalable software management within the European bioinformatics infrastructure.

TODO: Summarize key results, including outcomes from EDAM term mapping, curation insights, and future directions.

# Introduction

[Bioconductor](https://bioconductor.org/) is a globally recognized open-source project that provides over 2,000 packages for high-throughput genomic data analysis within the R programming environment. These tools support a vast range of bioinformatics applications, from differential gene expression analysis to visualization and data integration, making Bioconductor a critical resource for life sciences research. However, with the expansion of bioinformatics resources, there is a growing need for improved methods to locate and apply appropriate tools, particularly in complex data workflows.

The [ELIXIR Research Software Ecosystem (RSEc)](https://research-software-ecosystem.github.io/) supports the FAIR principles—Findability, Accessibility, Interoperability, and Reusability—and offers a structured approach to organizing bioinformatics tools through the bio.tools registry and the EDAM ontology. By aligning Bioconductor packages with these standards, we aim to enhance the discoverability and usability of these resources within the broader bioinformatics community.

This project focuses on mapping the biocViews taxonomy to EDAM terms, curating a subset of Bioconductor packages with manual annotations, and establishing pathways for automated synchronisation between Bioconductor and bio.tools. In addition to advancing the EDAM standard, this project will lay the groundwork for sustainable collaboration between the Bioconductor and ELIXIR communities. Through structured integration and community-driven development, this initiative represents a foundational step toward a cohesive and accessible bioinformatics ecosystem.

# Results

## Mapping biocViews terms with EDAM

Our work focused on mapping biocViews terms to the EDAM ontology, identifying gaps and inconsistencies between the two vocabularies. Unlike EDAM, biocViews is not structured as an ontology and has a broader, less standardized scope, which presents challenges in mapping specific concepts. This process revealed areas where EDAM could be extended or refined to better represent the domain covered by biocViews.

Some pre-hackathon groundwork on biocViews-to-EDAM mapping was performed using the `text2term` Python package, with preliminary results available [here](https://vjcitn.github.io/biocEDAM/articles/biocEDAM.html#a-preliminary-comparison-of-the-vocabularies). Building on this effort during the hackathon, the "biocViews mapping"" sheet ([linked here](https://docs.google.com/spreadsheets/d/155rJX5pUPFDIQNsX0AsohEjFjxfJ9za54b45V9gtQzg/edit?gid=1016157783#gid=1016157783)) now contains detailed annotations. The “mapping” column includes ongoing manual reviews with categories such as "mapped and relevant," "mapped but not relevant," "not mapped but mappable to EDAM term," "not mapped and no equivalent in EDAM," and "not mapped and out of EDAM scope."

## Clustering Bioconductor packages by biocViews

A clustering analysis was performed on Bioconductor packages based on their biocViews annotations to explore how they currently group. This analysis provides insights into existing thematic clusters within Bioconductor, highlighting similarities across packages and identifying areas where biocViews could be refined or extended for clearer categorization. The results of this clustering can also guide future EDAM term mappings to ensure alignment with these groupings and enhance package discoverability.

TODO: Add info from Aurelien and Ben.

## Defining a reference set of packages

We created an initial reference set of Bioconductor packages, accessible in the “Package list” sheet ([link](https://docs.google.com/spreadsheets/d/155rJX5pUPFDIQNsX0AsohEjFjxfJ9za54b45V9gtQzg/edit?gid=1269194852#gid=1269194852)). This includes well-known, heavily downloaded packages, as well as those suggested by project contributors and developers. The “Package curation” table ([link](https://docs.google.com/spreadsheets/d/155rJX5pUPFDIQNsX0AsohEjFjxfJ9za54b45V9gtQzg/edit?gid=1035911148#gid=1035911148)) was developed for annotating these packages with EDAM terms, to improve discoverability and integration with bio.tools. Contributors are encouraged to help populate the “should they be in bio.tools?” column and further refine the annotations.

Several package developers also reviewed and updated EDAM annotations in bio.tools for their packages, providing curated examples for future work, including:

-   [xcms](https://bio.tools/xcms)
-   [BridgeDbR](https://bio.tools/bridgedbr)
-   [rWikiPathways](https://bio.tools/rwikipathways)

## Integrate Bioconductor packages with ELIXIR RSEc

We have now incorporated Bioconductor metadata into the ELIXIR Research Software Ecosystem (RSEc) framework , with automatic weekly updates to facilitate ease of maintenance and integration. See [details here](https://github.com/research-software-ecosystem/content/tree/master/imports/bioconductor).

On the other hand, we discussed how EDAM annotations might find their way into R / Bioconductor packages as first class citizens. 
This could be as simple as having custom fields in `DESCRIPTION` with one or more EDAM topics. 
For information where the key:value schema of `DESCRIPTION` is insufficient, or to simply avoid bloating `DESCRIPTION`, it is possible to use a new, rich annotation file 
similar to the `CITATION` for bibliographic information, although the use of ontology terms and relations would make JSON-LD or RDF related formats more suitable. 
This new file could include information about operations and their input & output data and formats, similar to the information available from bio.tools. 
Such a file could The format could be inspired by Bioschemas [ComputationalTool](https://bioschemas.org/profiles/ComputationalTool/).
To improve the maintenance, Roxygen2 infrastructure and custom roclets could be used to collect the annotations directly from the R source code, 
similar to how `DESCRIPTION`, `NAMESPACE` and the manpages can be generated already today. 

## Automating EDAM annotation for Bioconductor packages

Prototyping is underway for a tool to automatically suggest EDAM terms based on Bioconductor package content. with initial explorations documented in [this vignette](https://vjcitn.github.io/biocEDAM/articles/curate.html). Following these explorations, a need was identified to refactor the Python code in [biocEDAM/inst/curbioc](https://github.com/vjcitn/biocEDAM/blob/main/inst/curbioc/curbioc.py) to streamline and modularize functionality, leading to the development of the `edamize()` function. Demonstrated on an [MSnbase vignette](https://vjcitn.github.io/biocEDAM/articles/curate.html#example-3-msnbase), `edamize()` marks an important step toward automating EDAM annotations, though it currently lacks robustness and requires further refinement.

An additional approach explored embedding Bioconductor package vignettes into a vector space, using OpenAI’s text-embedding-3-large model and visualizing the results through PCA. Using the reference set of 37 packages identified during the BioHackathon (detailed in the Defining a reference set of packages section), we observed some thematic clustering, revealing similarities across package descriptions that could assist with EDAM term suggestions. Embedding clusters could eventually be customized by EDAM’s top-level categories (e.g., "purpose," "inputs," "outputs"), further supporting user workflows in annotating packages with EDAM terms. This embedding-based approach, while in its early stages, shows potential for aiding both package authors and curators.
![Figure X: PCA of Bioconductor package embeddings from the curated reference set. Vignettes were embedded using OpenAI's text-embedding-3-large model, with each point representing a vignette. Packages with multiple vignettes appear multiple times. Observed clustering patterns may guide future categorization by top-level EDAM categories (e.g., "purpose," "inputs," "outputs") to support improved EDAM term suggestions.](figures/embeddings_PCA.png)  


To streamline EDAM annotations further, a potential enhancement was proposed (discussed above in the RSEc integration section): adding a [custom field in the DESCRIPTION file](https://r-pkgs.org/description.html#sec-description-custom-fields) for Bioconductor packages, allowing for EDAM terms (e.g., topics, operations, data types) to be recorded directly within the package metadata. Additionally, the [creation of a roclet](https://roxygen2.r-lib.org/articles/extending.html#creating-a-new-roclet) would enable developers to annotate packages with these EDAM terms directly in their code, using the Roxygen tool they already use for documentation. This approach would generate a structured metadata file similar to the operations graph in [bio.tools for xcms](https://bio.tools/xcms), allowing Bioconductor packages to be more precisely described for integration into bio.tools and enhancing discoverability within the ELIXIR ecosystem.

## Enhancing user querying of tools

A prototype of a [BioChatter](https://biochatter.org/) module was initiated to leverage the bio.tools API, enabling users to query Bioconductor package information more intuitively. The module interprets natural language questions, translates them into bio.tools API calls, and retrieves relevant package details based on EDAM terms and other metadata. This approach is intended to support complex, context-specific queries, enhancing users' ability to identify suitable Bioconductor tools for particular bioinformatics applications.

To advance BioChatter, we are seeking specific user questions and expected outcomes to develop well-defined use cases. These examples will guide the API’s natural language processing capabilities and refine responses, ensuring alignment with user needs.

# Discussion

# Conclusions

# Future work

Establish guidelines for the annotation of Bioconductor packages in bio.tools....

# Links to software

(e.g., GitHub or Jupyter Notebooks) and data repositories created or developed during the event)

...

## Acknowledgements

This work was performed during the ELIXIR BioHackathon Europe 2024 organised by ELIXIR in November 2024. This work was supported by [ELIXIR](https://elixir-europe.org/), the research infrastructure for life science data. CR is part of the Institut Français de Bioinformatique (IFB, UAR 3601), funded by the Programme d'Investissements d'Avenir subsidised by the Agence Nationale de la Recherche, number ANR-11-INBS-0013. This work was supported in part by NHGRI U24HG004059 "Bioconductor: An Open-Source, Open-Development Computing Resource for Genomics". This project has been made possible in part by grants 2024-XXX (TODO: Add Vince's CZI EOSS6 grant id), 2024-342819 and 2024-342820 from the Chan Zuckerberg Initiative DAF, an advised fund of Silicon Valley Community Foundation. 

...

## References
