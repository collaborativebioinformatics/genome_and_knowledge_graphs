# Eight Community Recommendations for Genome and Knowledge Graph Infrastructure Elements


## Authors


Ahmed M. Moustafa*
moustafaam@email.chop.edu
ORCID: 0000-0002-9949-6936
Division of Pediatric Infectious Diseases, Children's Hospital of Philadelphia
3615 Civic Center Boulevard, Philadelphia, PA 19104


Vlad Korolev*
vkorol1@umbc.edu
ORCID: 0000-0003-4497-9575
Dept of Computer Science and Electrical Engineering, UMBC
1000 Hilltop Circle, Baltimore, MD 21250


Surya Saha*
ss2489@cornell.edu
ORCID: 0000-0002-1160-1413
School of Animal and Comparative Biomedical Sciences, The University of Arizona
1117 E. Lowell Street, ACBS Building 90, Tucson, AZ 85721
Boyce Thompson Institute
533 Tower Road, Ithaca, NY, 14853


Robert Davey*
robert.davey@earlham.ac.uk
ORCID: 0000-0002-5589-7754
Earlham Institute
Norwich Research Park
Norwich, UK, NR4 7UZ


Jerven Tjalling Bolleman*
jerven.bolleman@sib.swiss
ORCID: 0000-0002-7449-1266
Swiss-Prot group
Swiss Institute of Bioinformatics
Rue Michel Server 1
1201 Geneve 4
Switzerland


Robert A. Edwards*
redwards@sdsu.edu
ORCID: 0000-0001-8383-8949
Department of Biology, San Diego State University, 
5500 Campanile Dr, San Diego, CA 92109


Alex Gener 
Baylor College of Medicine


Felix Shaw
Felix.Shaw@earlham.ac.uk
ORCID: 0000-0001-9649-5906
Earlham Institute
Norwich Research Park
Norwich, UK, NR4 7UZ


Nuala A. O’leary
olearyna@ncbi.nlm.nih.gov
National Center for Biotechnology Information (NCBI), National Library of Medicine, NIH
8600 Rockville Pike, Bethesda MD, 20894 USA


Nicholas P. Cooley
npc19@pitt.edu
ORCID: 0000-0002-6029-304X
Department of Biomedical Informatics, University of Pittsburgh School of Medicine
5607 Baum Boulevard, Pittsburgh, PA 15206


Joyce Lee
jlee@bionanogenomics.com
ORCID: 0000-0002-3492-1102
Bionano Genomics
9540 Towne Centre Dr, San Diego, CA 92121


Yuriy Skripchenko
skripche@ncbi.nlm.nih.gov
National Center for Biotechnology Information (NCBI), National Library of Medicine, NIH
8600 Rockville Pike, Bethesda MD, 20894 USA


Jason Williams
williams@cshl.edu
ORCID: 0000-0003-3049-2010
Cold Spring Harbor Laboratory
1 Bungtown Rd. 
Cold Spring Harbor, NY 11724


Fernanda Foertter
ffoertter@nvidia.com 
ORCID:  0000-0002-8906-3176
NVIDIA Corp. 
2788 San Tomas Expy
Santa Clara, CA 95051


Vito Adrian Cantu
vcantualessioroble@sdsu.edu
ORCID: 0000-0002-3168-5140
Computational science research center, San Diego State University, 
5500 Campanile Dr, San Diego, CA 92182


Sonia Gavasso
sonia.gavasso@uib.no
sgavasso@stanford.edu
Haukeland University Hospital 
Department of Clinical Medicine and Neurology
5021 Bergen, Norway
Stanford University Medical Center
Department of Anesthesia
Stanford , CA 94305


Ben Busby
bbusby@dnanexus.com
ORCID: 0000-0001-5267-4988
National Center for Biotechnology Information (NCBI), National Library of Medicine, NIH
8600 Rockville Pike, Bethesda MD, 20894 USA
Current Address: DNAnexus, Mountain View, CA

## Abstract


The genome sequence for a species has traditionally been represented as a linear consensus string of bases that has been sourced from a ‘reference individual’ or group of individuals. These models are  limited and conform to a simplified two dimensional representation  of linear chromosome structure but are widely supported by nearly all bioinformatics software tools used for sequence analysis. Major drawbacks include the omission of potentially interesting subsequences and structural variants  from a particular individual which fall outside a given reference genome . A graph can be used to retain this natural variation, in a number of data structures, one such is called a variation graph. Variation graphs can support multiple versions of sequences from the same organism or a population, thus allowing analysis of all of the genome(s) of interest, i.e. a pangenome.
  
The use of graph structures for pangenomes is relatively new in the life sciences, therefore there are few tools to build, assess, and interrogate them. There are even fewer tools or infrastructure elements for collecting, associating and deriving scientific value from metadata associated with graphs. This situation is also exacerbated by a lack of widely accepted community standards for describing pangenomes and underlying data structures. Here we present ten recommendations for tools or infrastructure development that should enable maximum value from pangenomic data and analyses.
Keywords
Graph genome, knowledge graph, pangenome, structural variation




## Introduction


Importance of pangenomes to handle the flood of genome assemblies being produced


Value of pangenomes for different domains of life


Pangenomes are especially useful for scientists investigating organisms or communities with complex genomic structure.  A specific example of the former are organisms with high ploidy, such as plants, where the copy number and subgenome location has functional consequences. An example of the latter  are metagenomic communities, consisting of thousands of species of bacteria, viruses, fungi and archaea.  


In plants, sequential selective breeding of cultivated populations (cultivars) results in the loss of many desirable traits like fruit color, flavor, and ripening (often found in wild counterparts). Diversity within and between highly bred “elite” varieties and their wild relatives is often described not as sequences at the genomic level but as quantitative trait loci (QTL) falling between observed markers (that themselves are increasingly sequenced with cheap, fast, genotyping-by-sequencing technologies). To locate and access traits, marker-based approaches  fall short of nucleobase  resolution. In this regard, plant genomes differ from humans and microbes in their genome size, complexity, ploidy, and restrictions on access to information from private breeding trials. When whole genome sequencing (WGS) is used, efforts tend to produce a single linear reference, typically draft because of funding constraints or difficulties due to the above genomic properties. Graphs instead , offer a system to encapsulate genomic diversity in a species within a single composite data structure. Data from tomato breeding was anchored on the Heinz 1706 reference for many years until genomes for wild species were reported recently (REF[b][c]). Similarly, the Chinese Spring hexaploid bread wheat linear reference genome sequence is now in its second version (RefSeq 2.0 REF[d]), and more genomes are being generated rapidly (10+ wheat genomes, OWWC[e], REFS[f]). Graph representations of these pangenomes will improve the power of comparative analysis to discover the inheritance and propagation of traits of interest through the evolutionary tree across time. Current crop genome references do not represent many of the traits of interest when a breeder is evaluating trials. Graph reference genomes[g] - reference genome-independent graph representations of the genomic complexity in the species will allow the breeder to accurately find the loci associated with the trait of interest.


In the microbial field, the pangenome term was first introduced by Tettelin et al. in 2005. Simply, a pangenome is the union of genes that are shared by a collection of genomes. It is composed of core genes that are present in all genomes, accessory genes that are present in two or more genomes, and unique genes that are present in one genome. Interestingly some bacterial species have been shown to have open pangenomes where horizontal gene transfer keeps adding to the diversity of the species (Vernikos et al. 2015). The pangenome definition was recently expanded by the Computational Pan-Genomics Consortium to be the collection of genome sequences that will be analyzed; to classically identify the set of genes present in a dataset at hand or to be used as a reference to improve read mapping and variant calling. On the other hand, a metagenome is the genomic content of cultured and uncultured microorganisms sampled from an environment. 



Plus viruses [h][i]


We need a short paragraph about animal genomes, particularly complex communities (lets go with 1000 bulls?)[j][k][l][m]


Similar to plants, pangenomes in humans and other animals are categorized as…. 


Need a paragraph about human communities and disease[n][o][p]


Doesn't make sense 20 years post-genome to be aligning to one person's genome and calling/making disease associations for disparate populations based on that. 


1.        Pangenomic Pipeline Submission System[q][r]
Data access and reuse is paramount for scientific robustness and reproducibility. The FAIR principles outline a core ideology for data and software (REF[s]). For pangenomes to be FAIR, data needs to be deposited in a suitable repository via a  standardized approach with all metadata needed to describe and reproduce the results. A submission system should submit all novel raw data along with rich sample metadata used in the analysis to a public archive such as the INSDC repositories (NCBI/EBI/DDBJ). Novel assemblies and gene calls that stem from a pangenome graph should also be submitted with an optional annotation in a community-accepted format. Ideally, the metadata will be in structured, standardized format for ease of validation and indexing by the public archives receiving these submissions. All data that originated from public archives must retain their accession numbers and version identifiers in order to increase interoperability and encourage federated data access and prevent duplicate underlying datasets. Regardless of which public archive the data is submitted to, the data should be locatable through standardized data location protocol such as those proposed by GA4GH. As public data archives become more prevalent and specialized it is imperative that their users can interact with them in a standardized way to lower the barrier of searching and accessing the data. Metadata-aware semantic data submission systems exist, e.g.  COPO (copo-project.org), that could be developed to support  pangenomic submissions. Once a pangenome metadata schema and endpoint is formalized such systems will need to implement this specification.


2.        A System to Annotate and Support Genome Graphs with Traditional Genomic, Phenotypic, and Other Data Types[t][u]


In addition to the tools that create and update pangenomes graphs, tools are needed that can organize the metadata associated with both the overall graph structure and with each node. Such metadata would be represented in layers on the top of the variation graph. These data could be SNP-CHIPs, RNA-Seq, proteins, phylogenetic trees, phenotypes, crystallographic and Cryo-EM images of proteins, epidemiological data or even literature for a particular event. Such tools should create unique identifiers (IRIs) for the metadata, which  themselves could be represented  in a graph, and associated with corresponding nodes or the variation graph itself. A node accession system needs developing. Such accessions could be hashed signature values that comprise all metadata for a node, e.g. a stable node accession system encoding the node history in its name ( https://github.com/vgteam/vg/wiki/Stable-Deterministic-Node-identifiers-by-encoding-edit-history-in-Node-name-identity). An alternative would be to combine the path of a given node, the offset from the start of that path, and the node length (e.g. http://example.org/path/hg39-X/node/100/length/10). Therefore when the node exists in multiple paths, multiple IRIs will point to that node.




3.        A System to Derive Constituent Sequences from Pangenomes


Aka “slicing horizontally”


Pangenomes can be explored within and between species to address pertinent biological problems, such as gene sets to identify trends in subpopulations, disease susceptibility, or genetic basis for any phenotype. The pangenome can be used to analyze and visualize reduced datasets. The user will need to be able to query and retrieve sequence data and metadata of interest for further analysis and be able to map back to the pangenome graph.


Example: You want to know the variation of HLA genotypes of blue zone centenaries across different continents. By constructing a pangenome, the sequence data in the path is significantly reduced to regions of variation/uniqueness that can be further interrogated by a research scientist.


Here is a live example of that in action, the annotation and full URL can be accessed from https://bit.ly/38TYESD:


  







4.        A System to Derive Node Combinations from Graphs


Aka -- “slicing vertically” 
 
The pangenome data structure allows users to identify haplotypes containing a particular feature on the genome (such as  a gene, SNP, trait marker or non-genic functional element). By being able to traverse node combinations for any sequence they can easily identify other characteristics of a haplotype. This will lead to the discovery of new elements within a haplotype that could be overlooked in a linear genome view. Pangenomic analysis can enable advanced classification of population subgroups faster and allows the exploration of features in detail along the path of interest. This will be useful to agricultural researchers and breeders, who need access to phased haplotypes when deciding on germplasm to take forward in trials.


In the different types of graphs and use cases outside plants!
5.        RDF Representation of Annotation Relationships (Knowledge Graphs)[v]
        


Being interoperable, a pan-genome representation will be linkable to existing resources. 
While graph genomes allow for new measures of orthology (e.g. fraction of nodes shared between gene paths), the aim is to allow reuse of existing resources such as BUSCO[w][x][y][z][aa][ab]. This means that these data sets should be interoperable. A straightforward approach is to use RDF views on both datasets. BUSCO output is available as RDF as are classical orthology databases as OrthoDB(REF)[ac] and OMA(REF)[ad]. The same is true for other important annotation sources such as UniProt and Ensembl as well as the ontologies used to annotate such as the Gene Ontology.


Annotations inside the pangenome graphs will be related via new links using the paths as an anchoring point.


While an RDF view is practical for interoperability, we expect the storage to be in highly compressed formats with annotations being in optimized independent systems. To work, each annotated item needs to have a stable identifier that is globally resolvable. Such stable identifiers are derivable from the graph content (see section 2.). While graph genome formats can be extended to contain annotations, doing so would make the storage optimization much more complicated.


Some new annotations will be for subgraphs. For example, a collection of gene paths that represent the same conceptual “gene” even if the encoding is different. Such subgraphs might even be probabilistic data structures in their own right. Such subgraphs should be identifiable in their own right. The SPARQL named graph concept can be used to group nodes and edges in such a subgraph into an accessible and defined set.


Knowledge management systems store facts about the real world in a graph type of structure.   RDF, mentioned in other sections, is a standard framework for expressing such graphs.   However, especially in life sciences, there is no hard consensus regarding many facts,  especially newly discovered ones.   Multiple contradictory opinions can exist about the exact mechanisms of specific gene expression.  A sound knowledge management system must accommodate for the existence of multiple opinions about the same fact, and provide a mechanism to rank-order the facts to fulfill the needs of a particular user who is querying a system.


Knowledge graphs can also be represented as hyper graphs where nodes represent any kind of assertions (accession number, date of collection, isolation source, etc.). Different types of edges can express different relationships between those assertions. “Genome Edges” represent genomes and include all the assertions that are true for that genome. “Categorical Edges” allow grouping of nodes by category, for example grouping all accession numbers in a single edge. “Relationship Edges” describe known relationships between assertions, for example if a set of SNPs is correlated to a disease. Finally “Query Edges” are constructed on the fly and represent a subset of assertions that the user is interested in, for example “all the isolation dates this year”.


One can therefore construct a genome graph using the genomes represented by edges that intersect any number of categorical, relationship, and/or query edges. 




6.        A Query System for Knowledge-Object Relations[ae]


Graphs of pangenomes and related annotations open up the possibility of developing a public query service that could provide answers to human-level queries, such as:


Given these sequences of Penaeus monodon specimen that is known to exhibit a trait of resistance to WSSV infection, I want to know about differential gene expression studies related to this region of the pan-genome in the related species.  


However, the implementation of such a system is possible only if the following conditions are met:   


* Both sequence object and knowledge object data are stored in a form where each node or edge is addressable using commonly accepted addressing method such as IRI. 


* There exists a pan-genome coordinate system that is independent of any particular organism. Such a coordinate system could be based on the distance to known stable sub-sequences in the genome and expressed as a vector. 


* There is a query language that is capable of traversing both knowledge and genome graphs.




Because the genomic data is collected, curated, and stored by several international organizations, it would be beneficial to the researcher to submit queries that span services from multiple organizations.  Therefore the query service must allow for the handling of federated requests.


Existing tools could be adapted to implement such a service easily. Currently SPARQL is the only query language with multiple implementations that support federated querying.


The query language will need to support fuzzy matches that are tolerant to slight variations between the query string and search data. Such augmentations can be implemented using existing techniques such as sequence alignment algorithms or probabilistic semantic web reasoners. An alternative is to have named functions for common bioinformatics commands. Such functions can be implemented by our community as needed.


7.        Publish the recipe, not the cheesecake[af][ag][ah][ai]


With the goal of conforming to FAIR data practices, a set of recommendations in relation to the construction of data-sets, tools, and complex analysis are as follows:
1. Pipelines and scripts involved in the construction of any published results should be available in a publication and open access.
2. New and novel tools should be accompanied by a container - such as Docker or Singularity - upon publication.
3. New and novel tools should not be dependent upon specific parallelization or high performance computing architectures or topologies.
4. Relevant metadata and source data should be easily obtainable from published work through unique publicly-resolvable identifiers.
5. Clear documentation and vignettes that are conceptually accessible to reviewers, target users of a tool, and investigators in adjacent fields.
These recommendations have been distilled from chaotic and colorful discussions about how the bioinformatics community should be approaching its future. The current academic bioinformatics community is vibrant, well trained, and interdisciplinary, but geographically disparate, beholden to a multitude of funding strings, and unable to compete with private sector salaries. These strengths and stressors lead to one of the major challenges in bioinformatics; a wealth of useful ideas and projects coupled with the lack of a strongly maintained and cleanly interoperable ecosystem of analytical tools. This problem will only intensify as access to high-performance and high-throughput computing increases, data storage costs decrease, and the field itself evolves and grows to gain interest in new or currently unforeseen scientific questions or conceptual tools.
The authors here emphatically disagree with philosophies arguing for the supremacy of specific scripting languages and high level organizational schemes, or specific tools. Diversity of conceptual and technical training are a strength that the field would do well to maintain. These recommendations have been compiled in an attempt to convince the field to bend it’s collective will towards interoperable and replicable systems in general.
8.        Pangenome in a Bottle


Besides defining effective practices and recommendations for pangenomics, we will focus on available breeding resources that can be used to benchmark pangenomics tool kits. Large scale breeding efforts in the widely cultivated crops such as maize, provide some of the most complex but well characterized breeding populations. The nested association mapping population (NAM) in maize is one of the best characterized sets of parental lines in agricultural cropping systems and forms the basis of a number of breeding efforts in the maize community. This can serve as a rich validation data set for evaluating the data sets for study of impact of domestication on fruit size, color and disease resistance. 


Conclusion:  
Comparison to enhanced multiple available variant sets is a strategy that leverages taking these principles into account is encompassed in a prototype built several months later in an ELIXIR BioHackathon
References: 






Kim, D., Paggi, J.M., Park, C. et al. Graph-based genome alignment and genotyping with HISAT2 and HISAT-genotype. Nat Biotechnol 37, 907–915 (2019). https://doi.org/10.1038/s41587-019-0201-4




Tettelin, H; Masignani, V; Cieslewicz, M. J.; Donati, C; Medini, D; Ward, N. L.; Angiuoli, S. V.; Crabtree, J; Jones, A. L.; Durkin, A. S.; Deboy, R. T.; Davidsen, T. M.; Mora, M; Scarselli, M; Margarit y Ros, I; Peterson, J. D.; Hauser, C. R.; Sundaram, J. P.; Nelson, W. C.; Madupu, R; Brinkac, L. M.; Dodson, R. J.; Rosovitz, M. J.; Sullivan, S. A.; Daugherty, S. C.; Haft, D. H.; Selengut, J; Gwinn, M. L.; Zhou, L; et al. (2005). "Genome analysis of multiple pathogenic isolates of Streptococcus agalactiae: Implications for the microbial "pan-genome"". Proceedings of the National Academy of Sciences. 102 (39): 13950–5. Bibcode:2005PNAS..10213950T. doi:10.1073/pnas.0506758102. PMC 1216834. PMID 16172379


A couple of historic papers - 8 genomes!!
Medini D, Donati C, Tettelin H, Masignani V, Rappuoli R. 2005. The microbial pan-genome. Curr Opin Genet Dev 15:589–594.
https://www.sciencedirect.com/science/article/pii/S0959437X05001759




This has 573 genomes:
Lapierre P, Gogarten JP. 2009. Estimating the size of the bacterial pan-genome. Trends Genet 25:107–110. https://www.sciencedirect.com/science/article/pii/S0168952509000055


Anti-virulence genes
Bliven KA, Maurelli AT. 2012. Antivirulence genes: insights into pathogen evolution through gene loss. Infect Immun 80:4061–4070.
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3497401/


Approaches and reviews for pangenomics


Computational Pan-Genomics Consortium. 2018. Computational pan-genomics: status, promises and challenges. Brief Bioinform 19:118–135.
https://academic.oup.com/bib/article/19/1/118/2566735


Snipen L, Almøy T, Ussery DW. 2009. Microbial comparative pan-genomics using binomial mixture models. BMC Genomics 10:385.
https://bmcgenomics.biomedcentral.com/articles/10.1186/1471-2164-10-385


Snipen L, Ussery DW. 2010. Standard operating procedure for computing pangenome trees. Stand Genomic Sci 2:135–141.
https://environmentalmicrobiome.biomedcentral.com/articles/10.4056/sigs.38923


Tettelin H, Riley D, Cattuto C, Medini D. 2008. Comparative genomics: the bacterial pan-genome. Curr Opin Microbiol 11:472–477.
https://www.sciencedirect.com/science/article/pii/S1369527408001239


Vernikos G, Medini D, Riley DR, Tettelin H. 2015. Ten years of pan-genome analyses. Curr Opin Microbiol 23:148–154.
http://www.sciencedirect.com/science/article/pii/S1369527414001830


Tools for microbial pangenomes


Page AJ, Cummins CA, Hunt M, Wong VK, Reuter S, Holden MTG, Fookes M, Falush D, Keane JA, Parkhill J. 2015. Roary: rapid large-scale prokaryote pan genome analysis. Bioinformatics 31:3691–3693. 
https://academic.oup.com/bioinformatics/article/31/22/3691/240757


PPanGGOLiN: Depicting microbial diversity via a Partitioned Pangenome Graph
Guillaume Gautreau, Adelme Bazin, Mathieu Gachet, Rémi Planel, Laura Burlot, Mathieu Dubois, Amandine Perrin, Claudine Médigue, Alexandra Calteau, Stéphane Cruveiller, Catherine Matias, Christophe Ambroise, Eduardo PC Rocha, David Vallenet
bioRxiv 836239; doi: https://doi.org/10.1101/836239 


Xiao J, Zhang Z, Wu J, Yu J. A brief review of software tools for pangenomics. Genomics Proteomics Bioinformatics. 2015 Feb;13(1):73-6. doi: 10.1016/j.gpb.2015.01.007. Epub 2015 Feb 23. PMID: 25721608; PMCID: PMC4411478. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4411478/ 


Laing C, Buchanan C, Taboada EN, Zhang Y, Kropinski A, Villegas A, Thomas JE, Gannon VPJ. 2010. Pan-genome sequence analysis using Panseq: an online tool for the rapid analysis of core and accessory genomic regions. BMC Bioinformatics 11:461.
https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-11-461


Huang K, Brady A, Mahurkar A, White O, Gevers D, Huttenhower C, Segata N. 2014. MetaRef: a pan-genomic database for comparative and community microbial genomics. Nucleic Acids Res 42:D617–24.
https://academic.oup.com/nar/article/42/D1/D617/1047917


Bayliss SC, Thorpe HA, Coyle NM, Sheppard SK, Feil EJ: PIRATE: A fast and scalable pangenomics toolbox for clustering diverged orthologues in bacteria. Gigascience 2019, 8. https://academic.oup.com/gigascience/article/8/10/giz119/5584409


Peng Y, Tang S, Wang D, Zhong H, Jia H, Cai X, Zhang Z, Xiao M, Yang H, Wang J, et al.: MetaPGN: a pipeline for construction and graphical visualization of annotated pangenome networks. Gigascience 2018, 7.
https://academic.oup.com/gigascience/article-lookup/doi/10.1093/gigascience/giy121


Zhao Y, Wu J, Yang J, Sun S, Xiao J, Yu J. 2012. PGAP: pan-genomes analysis pipeline. Bioinformatics 28:416–418.
https://academic.oup.com/bioinformatics/article/28/3/416/188161


Chaudhari NM, Gupta VK, Dutta C. 2016. BPGA- an ultra-fast pan-genome analysis pipeline. Sci Rep 6:24373.
https://www.nature.com/articles/srep24373


Contreras-Moreira B, Vinuesa P. 2013. GET_HOMOLOGUES, a versatile software package for scalable and robust microbial pangenome analysis. Appl Environ Microbiol 79:7696–7701.
https://aem.asm.org/content/79/24/7696.short


Snipen L, Liland KH. 2015. micropan: an R-package for microbial pan-genomics. BMC Bioinformatics 16:79.
https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-015-0517-0


Benedict MN, Henriksen JR, Metcalf WW, Whitaker RJ, Price ND. 2014. ITEP: an integrated toolkit for exploration of microbial pan-genomes. BMC Genomics 15:8.
https://bmcgenomics.biomedcentral.com/articles/10.1186/1471-2164-15-8




qqTools for plant pangenomes




Practical haplotype graphs ( PHG, https://bitbucket.org/bucklerlab/practicalhaplotypegraph/wiki/Home) defines anchor and non-anchor ranges with respect to ta reference genome. The anchor regions are typically genes that are conserved between accessions and transitions probababilities are defined between anchor haplotypes for a given population. Short reads can be aligned to the anchor genic regions with off the shelf tools such as GATK [REF]. This approach can be used to infer high-density genotypes directly from low-coverage sequence from a breeding population. This approach is being used by the wheat and maize communities to capture the diversity in breeding populations. PHG has an API and database schema available for implementation.


  
   










GLOSSARY 
* Placeholder for the suggestion that we have a glossary of terms (see the margins of this paper as an example: https://www.nature.com/articles/35080529.pdf )


Conclusion and next steps
This section should include a brief discussion of allowances made (if any) for controlling bias or unwanted sources of variability, and the limitations of any novel datasets. 


Tools Suggestions
We propose a Pangenome Pipeline Submission System that would need the following.
  

1. Assembly
2. Annotation (PGAP)
   1. Gene calling
Data and software availability
Source code for new software must be made openly, and permanently available in a structured repository such as Zenodo (the F1000Research team can assist with deposition), as well as uploaded to a Version Control System (VCS) such as GitHub, BitBucket or SourceForge. Please provide details in a section entitled “Software availability”, listing the repository and the license under which the software can be used in the article. Source code must be assigned an open license. 


Suggested Reviewers


Please pick ten suggested reviewers with whom you have not published in the last three years and who do not work in the same department.  Papers can not be sent to F1000 research without such a list.  
Competing interests
Note any financial, personal, or professional competing interests for any of the authors that could be construed to unduly influence the content of the article. If none, include the text ‘No competing interests were disclosed.’
Grant information
Include funding if relevant (including funding from authors’ employers if relevant, and any relevant grant funding).  If none, include the text ‘The author(s) declared that no grants were involved in supporting this work’. 


Jerven Bolleman and Swiss-Prot activities are supported by the Swiss Federal Government through the State Secretariat for Education, Research and Innovation SERI, and the Swiss National Science Foundation (SNSF).
Acknowledgements
This section should acknowledge anyone who contributed to the research or the writing of the article but who does not qualify as an author; please clearly state how they contributed. Authors should obtain permission to include the name and affiliation, from all those mentioned in the Acknowledgments section.
References
Instructions on using the F1000R Google docs plug in for reference management: http://f1000.com/work/faq/google-docs-add-on/1


Instructions on using the F1000R Word plug in for reference management: http://f1000.com/work/faq/word-plugin 
Figures and Tables
All figures and tables should be cited and discussed in the article text. Figure legends and tables should be added at the end of the manuscript. Tables should be formatted using the ‘insert table’ function in Word, or provided as an Excel file. Files for figures should be uploaded as separate files through the submission system. Each figure or table should have a concise title of no more than 15 words. A legend for each figure and table should also be provided that briefly describes the key points and explains any symbols and abbreviations used. The legend should be sufficiently detailed so that the figure or table can stand alone from the main text. 


[a]We're almost there!  Need references and conversion to Markdown or latex


ala


https://github.com/biohackrxiv/submission-templates/blob/master/paper.md
[b]REF
[c]This one? https://www.frontiersin.org/articles/10.3389/fpls.2018.01402/full


AUTHOR=Razali Rozaimi, Bougouffa Salim, Morton Mitchell J. L., Lightfoot Damien J., Alam Intikhab, Essack Magbubah, Arold Stefan T., Kamau Allan A., Schmöckel Sandra M., Pailles Yveline, Shahid Mohammed, Michell Craig T., Al-Babili Salim, Ho Yung Shwen, Tester Mark, Bajic Vladimir B., Negrão Sónia
         
TITLE=The Genome Sequence of the Wild Tomato Solanum pimpinellifolium Provides Insights Into Salinity Tolerance  
        
JOURNAL=Frontiers in Plant Science     
        
VOLUME=9      
        
YEAR=2018
        
PAGES=1402   
                
URL=https://www.frontiersin.org/article/10.3389/fpls.2018.01402     
          
DOI=10.3389/fpls.2018.01402    
        
ISSN=1664-462X
[d]REF
[e]?
[f]REFS
[g]Genomes - plural. Consider mentioning nuclease vs approximate k-mer graphs along the lines of our SWIGG discussion. nucleobase graphs summarize all info, in a set of linear references. Alternative to VCF. They get unwieldy due to size. Approximate graphs threshold out less common variants, allowing observers to focus on common genomic features independently of whether biological feature annotation is available for a given biological entity.
[h]+npc19@pitt.edu
_Assigned to npc19@pitt.edu_
[i]+raedwards@gmail.com
[j]+olearyna@ncbi.nlm.nih.gov
_Assigned to nuala oleary_
[k]We can just mention FAANG and that they are trying to do similar things
[l]+suryasaha@gmail.com will ping FAANG and see if they want in?
_Reassigned to Surya Saha_
[m]I'll add to the animal section  - Sonja - I hope you made it out of quarantine +gavasso@yahoo.com
[n]@ben.busby@gmail.com
_Assigned to Ben Busby_
[o]Thats me!  Complex disease and cancer and graphs
[p]+eric.t.dawson@gmail.com ping
[q]Mention GA4GH TRS
[r]@ben.busby@gmail.com
[s]REF
[t]Can this be next to section 5 as it overlaps in parts.
[u]Any objections to renumbering?
[v]@vkorol1@umbc.edu
_Assigned to Vladimir Korolev_
[w]Cite the busco4 paper and very new RDF representation.
[x]add links to pubmed for citations and I'll take care of it.
[y]https://www.ncbi.nlm.nih.gov/pubmed/31020564
[z]Schema url is https://busco-data.ezlab.org/schema/
[aa]Could this also include gene family analysis, and not just core genes?
[ab]Yes? Not sure, what Busco/OrthoDB/Oma include in their models today. Pragmatically they are Protein orientated. So we need a link from Gene->Transcript->Protein to work with them as they are right now.
[ac]TODO
[ad]TODO
[ae]@moustafaam@email.chop.edu
_Assigned to Ahmed Moustafa_
[af]This should either be #1 or #10
[ag]Lets finish the bullet points and then decide on order?
[ah]and I agree
[ai]penultimate @ben.busby@gmail.com
