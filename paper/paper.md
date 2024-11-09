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

This project seeks to enhance the ELIXIR Research Software Ecosystem (RSEc) by increasing the findability, accessibility, interoperability, and reusability (FAIR principles) of Bioconductor’s extensive collection of over 2,000 bioinformatics packages. By aligning Bioconductor metadata with the EDAM ontology and integrating detailed package descriptions into the bio.tools registry, we aim to improve the discoverability and usability of genomic analysis tools. Short-term goals include mapping EDAM terms to Bioconductor’s biocViews taxonomy, developing a set of manually annotated “gold standard” packages, and evaluating tools for automated EDAM term suggestions. Long-term, we intend to expand EDAM coverage across Bioconductor, phase out biocViews, and implement automated synchronisation with bio.tools. This initiative fosters collaboration between Bioconductor and ELIXIR, establishing a foundation for sustainable software management in European bioinformatics. Key results include substantial progress in mapping EDAM terms to Bioconductor’s biocViews taxonomy, initiating the curation of a reference set of packages with manual annotations, integrating Bioconductor metadata into the ELIXIR Research Software Ecosystem (RSEc) with automated updates, and prototyping a tool for automated EDAM term suggestions. Together, these achievements establish a strong foundation for further integration and refinement.

# Introduction

[Bioconductor](https://bioconductor.org/) is a globally recognized open-source project that provides over 2,000 packages for high-throughput genomic data analysis within the R programming environment. Supporting a vast range of bioinformatics applications, these tools are widely used for gene expression analysis, visualization, and data integration, making Bioconductor a critical resource for life sciences research. However, the expanding bioinformatics landscape calls for enhanced methods to locate and apply appropriate tools, especially in complex workflows.

The [ELIXIR Research Software Ecosystem (RSEc)](https://research-software-ecosystem.github.io/) promotes the FAIR principles—Findability, Accessibility, Interoperability, and Reusability—and uses bio.tools and the EDAM ontology to organise bioinformatics tools. Aligning Bioconductor packages with these standards aims to enhance tool discoverability within the broader bioinformatics community.

This project focuses on mapping the biocViews taxonomy to EDAM terms, curating a subset of Bioconductor packages with manual annotations, and establishing pathways for automated synchronisation between Bioconductor and bio.tools. Beyond advancing the EDAM standard, this initiative builds a collaborative bridge between Bioconductor and ELIXIR. Through structured integration and community-driven development, this project represents a foundational step toward an accessible, interoperable bioinformatics ecosystem.

# Results

## Mapping biocViews terms with EDAM

We mapped biocViews terms to the EDAM ontology, identifying gaps and inconsistencies between the two vocabularies. Unlike EDAM, biocViews lacks a strict ontology structure and has a broader scope, creating challenges in specific concept mapping. This process revealed potential areas where EDAM could expand to better cover biocViews terms.

Some initial mapping was done using the text2term Python package, with preliminary results [here](https://vjcitn.github.io/biocEDAM/articles/biocEDAM.html#a-preliminary-comparison-of-the-vocabularies). During the hackathon, the "biocViews mapping" sheet ([linked here](https://docs.google.com/spreadsheets/d/155rJX5pUPFDIQNsX0AsohEjFjxfJ9za54b45V9gtQzg/edit?gid=1016157783#gid=1016157783)) was updated with detailed annotations in categories such as "mapped and relevant," "mapped but not relevant," "not mapped but mappable to EDAM term," and "not mapped and out of EDAM scope."

## Clustering Bioconductor packages by biocViews

We conducted clustering analysis on Bioconductor packages based on their biocViews annotations to explore natural groupings and thematic clusters. This analysis highlighted similarities across packages and can be used to pinpoint areas where biocViews could be refined for improved categorisation. Results may guide EDAM term mappings to align with package clusters and boost discoverability.

TODO: Add info from Aurelien and Ben.

## Defining a reference set of packages

We created a reference set of 37 Bioconductor packages, accessible in the “Package list” sheet  ([link](https://docs.google.com/spreadsheets/d/155rJX5pUPFDIQNsX0AsohEjFjxfJ9za54b45V9gtQzg/edit?gid=1269194852#gid=1269194852)), featuring well-known, heavily downloaded packages, as well as those suggested by project contributors and developers. This set serves as a basis for the  embedding-based analyses (described below), and the curation started in The “Package curation” table ([link](https://docs.google.com/spreadsheets/d/155rJX5pUPFDIQNsX0AsohEjFjxfJ9za54b45V9gtQzg/edit?gid=1035911148#gid=1035911148)).

Some package developers reviewed and updated EDAM annotations in bio.tools for their packages, providing curated examples for future work, such as:

-   [xcms](https://bio.tools/xcms)
-   [BridgeDbR](https://bio.tools/bridgedbr)
-   [rWikiPathways](https://bio.tools/rwikipathways)

## Integrate Bioconductor packages with ELIXIR RSEc

Bioconductor metadata now integrates with the ELIXIR Research Software Ecosystem (RSEc), with weekly automated updates. Details are [here](https://github.com/research-software-ecosystem/content/tree/master/imports/bioconductor).

On the other hand, we discussed how EDAM annotations might find their way into R / Bioconductor packages as first class citizens. 
This could be as simple as having custom fields in `DESCRIPTION` with one or more EDAM topics. 
For information where the key:value schema of `DESCRIPTION` is insufficient, or to simply avoid bloating `DESCRIPTION`, it is possible to use a new, rich annotation file 
similar to the `CITATION` for bibliographic information, although the use of ontology terms and relations would make JSON-LD or RDF related formats more suitable. 
This new file could include information about operations and their input & output data and formats, similar to the information available from bio.tools. 
Such a file could The format could be inspired by Bioschemas [ComputationalTool](https://bioschemas.org/profiles/ComputationalTool/).
To improve the maintenance, Roxygen2 infrastructure and custom roclets could be used to collect the annotations directly from the R source code, 
similar to how `DESCRIPTION`, `NAMESPACE` and the manpages can be generated already today. 

## Automating EDAM annotation for Bioconductor packages

Prototype development is underway for a tool to suggest EDAM terms based on Bioconductor package content. Initial work is documented in [this vignette](https://vjcitn.github.io/biocEDAM/articles/curate.html). The tool's Python code in [biocEDAM/inst/curbioc](https://github.com/vjcitn/biocEDAM/blob/main/inst/curbioc/curbioc.py) is being refactored, with a new `edamize()` function designed to improve automation of EDAM annotations, demonstrated on an [MSnbase vignette](https://vjcitn.github.io/biocEDAM/articles/curate.html#example-3-msnbase).

An additional approach explored embedding Bioconductor package vignettes into a vector space, using OpenAI’s text-embedding-3-large model and visualizing the results through PCA. Using the reference set of 37 packages identified during the BioHackathon (detailed in the Defining a reference set of packages section), we observed some thematic clustering, revealing similarities across package descriptions that could assist with EDAM term suggestions. Embedding clusters could eventually be customized by EDAM’s top-level categories (e.g., "purpose," "inputs," "outputs"), further supporting user workflows in annotating packages with EDAM terms. This embedding-based approach, while in its early stages, shows potential for aiding both package authors and curators.

![Figure X: PCA of Bioconductor package embeddings from the curated reference set. Vignettes were embedded using OpenAI's text-embedding-3-large model, with each point representing a vignette. Packages with multiple vignettes appear multiple times. Observed clustering patterns may guide future categorization by top-level EDAM categories (e.g., "purpose," "inputs," "outputs") to support improved EDAM term suggestions.](figures/embeddings_PCA.png)  


To record EDAM terms directly in Bioconductor packages, a potential enhancement was proposed (discussed above in the RSEc integration section): adding a [custom field in the DESCRIPTION file](https://r-pkgs.org/description.html#sec-description-custom-fields) for Bioconductor packages, allowing for EDAM terms (e.g., topics, operations, data types) to be recorded directly within the package metadata. Additionally, the [creation of a roclet](https://roxygen2.r-lib.org/articles/extending.html#creating-a-new-roclet) would enable developers to annotate packages with these EDAM terms directly in their code, using the Roxygen tool they already use for documentation. This approach would generate a structured metadata file similar to the operations graph in [bio.tools for xcms](https://bio.tools/xcms), allowing Bioconductor packages to be more precisely described for integration into bio.tools and enhancing discoverability within the ELIXIR ecosystem.

## Enhancing user querying of tools

A prototype of a [BioChatter](https://biochatter.org/) module was initiated to leverage the bio.tools API, enabling users to query Bioconductor package information more intuitively. The module interprets natural language questions, translates them into bio.tools API calls, and retrieves relevant package details based on EDAM terms and other metadata. This approach is intended to support complex, context-specific queries, enhancing users' ability to identify suitable Bioconductor tools for particular bioinformatics applications.

To advance BioChatter, we are seeking specific user questions and expected outcomes to develop well-defined use cases. These examples will guide the API’s natural language processing capabilities and refine responses, ensuring alignment with user needs.

# Discussion

This project has highlighted both the potential and complexities of aligning Bioconductor with the ELIXIR ecosystem. Mapping biocViews to EDAM offers a promising foundation for metadata standardisation, though manual review remains essential due to structural differences. The prototype for EDAM term suggestions and the embedding-based clustering provide a basis for further automation, while new annotation strategies for Bioconductor packages could simplify metadata integration. Our work with BioChatter shows promise for natural language queries of bio.tools data, pending further development based on user cases.

# Conclusions

Our integration of Bioconductor with the ELIXIR Research Software Ecosystem marks a foundational step toward enhanced discoverability and interoperability of bioinformatics tools. Mapping biocViews to EDAM, developing annotation prototypes, and exploring sustainable metadata practices have laid the groundwork for a cohesive bioinformatics ecosystem. Continued refinement and automation efforts will ensure Bioconductor resources are accessible and interoperable within ELIXIR’s infrastructure.

# Future work

Plans include automating Bioconductor metadata synchronisation with bio.tools, refining EDAM mappings across Bioconductor, and further developing our EDAM term suggestion prototype with improved term accuracy through embedding-based clustering. Additionally, we aim to enable Bioconductor package authors to enhance their package profiles directly in bio.tools, enriching metadata for the broader bioinformatics community. A roadmap through 2026 will guide these developments, ensuring ongoing collaboration with Bioconductor and ELIXIR communities.

# Links to software

This project utilised multiple resources to support the integration of Bioconductor packages within the ELIXIR Research Software Ecosystem.

The [biocEDAM GitHub repository](https://github.com/vjcitn/biocEDAM) served as the primary workspace for EDAM term mapping and developing the `edamize()` function for automated annotations.

Bioconductor metadata imports were added to the [ELIXIR RSEc GitHub repository](https://github.com/research-software-ecosystem/content/tree/master/imports/bioconductor).

The [Google Sheet of packages and terms ](https://docs.google.com/spreadsheets/d/155rJX5pUPFDIQNsX0AsohEjFjxfJ9za54b45V9gtQzg/edit?gid=1035911148#gid=1035911148) contains the curated reference package list, along with ongoing EDAM annotations and metadata. It also includes the results of manual reviews of automated biocViews-EDAM mappings, assessing the accuracy and relevance of each mapping.

(TODO: Add link for BioChatter bio.tools code if available, and some text eg: A BioChatter prototype module is in development to support natural language querying of Bioconductor packages via the bio.tools API, to be refined with additional use cases.)

## Acknowledgements

This work was performed during the ELIXIR BioHackathon Europe 2024 organised by ELIXIR in November 2024. This work was supported by [ELIXIR](https://elixir-europe.org/), the research infrastructure for life science data. CR is part of the Institut Français de Bioinformatique (IFB, UAR 3601), funded by the Programme d'Investissements d'Avenir subsidised by the Agence Nationale de la Recherche, number ANR-11-INBS-0013. This work was supported in part by NHGRI U24HG004059 "Bioconductor: An Open-Source, Open-Development Computing Resource for Genomics". This project has been made possible in part by grants 2024-XXX (TODO: Add Vince's CZI EOSS6 grant id), 2024-342819 and 2024-342820 from the Chan Zuckerberg Initiative DAF, an advised fund of Silicon Valley Community Foundation. 

...

## References
