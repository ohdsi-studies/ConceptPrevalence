Investigating Concept Heterogeneity and Granularity in the OHDSI Network
=============

<img src="https://img.shields.io/badge/Study%20Status-Design%20Finalized-brightgreen.svg" alt="Study Status: Design Finalized">

- Analytics use case(s): **Characterization**
- Study type: **Methods Research**
- Tags: **-**
- Study lead: **Anna Ostropolets**
- Study lead forums tag: **[aostropolets](https://forums.ohdsi.org/u/aostropolets)**
- Study start date: **March 15, 2019**
- Study end date: **-**
- Protocol: **[Word file](https://github.com/ohdsi-studies/ConceptPrevalence/extras/ConceptPrevalenceStudyProtocol_v1.0.docx)**
- Publications: **-**
- Results explorer: **-**

This study aims to investigate the concept usage patterns across different OHDSI datasets and their impact on cohort identification to facilitate cross-institutional and network studies. For every standard concept in the OMOP CDM, we will investigate if it is used at each site, and if used, which source code(s) are used at individual sites, and how differences in corresponding source codes impact the portability of cohort identification algorithms.  

Additional information
=============

In R, use the following commands to download and install:

install.packages("devtools")
devtools::install_github("https://github.com/ohdsi-studies/ConceptPrevalence")

library('ConceptPrevalence')

## Add inputs for the site:

dbms <- 'your_dbms'

user <- 'user'

password <- 'password'

server <- Sys.getenv('server')

port <- Sys.getenv('port')


cdmName <- 'your_cdm_name'

cdmDatabaseSchema <- 'your_cdm_schema

vocabDatabaseSchema <- 'your_vocab_schema'

resultDatabaseSchema <-"your_results_schema"


connectionDetails <- DatabaseConnector::createConnectionDetails(

							      dbms = dbms,
							      
                                                              server = server,
							      
                                                              user = user,
							      
                                                              password = password,
							      
                                                              port = port
							      
							      )
                                                              
## Then run the following:
ConceptPrevalence::calculate (

 				 connectionDetails,	
				 
  				 cdmName,
				 
				 cdmDatabaseSchema,
				 
 				 vocabDatabaseSchema,
				 
				 resultDatabaseSchema
				 )
			 
## Output

Once you run the package, you will see 5 csv files in your working directory (count_standard.csv, count_source.csv, mappings.csv, vocab_version.csv and cdm_info.csv).
You will then be able to send the files through a secure SFTP server.
Please contact me at ao2671 at cumc.columbia.edu to get the server credentials.

License
=======

ConceptPrevalence package is licensed under Apache License 2.0
