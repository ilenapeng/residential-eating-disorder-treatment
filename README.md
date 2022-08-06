# Residential Eating Disorder Treatment

This is the repository for my thesis on the expansion of residential eating disorder treatment centers.

## Repository contents
### Regulations - within the regulations folder
* download-fed-regulation.ipynb: Downloads 2021 state reports on regulations for adult mental health and substance use residential treatment centers from the Office of the U.S. Department of Health and Human Services’s Assistant Secretary for Planning and Evaluation. There are files for every state except Kentucky. The PDFs were then stacked to create all-state-regulations.pdf. To reduce the size of this GitHub repository, only the compiled PDF with all states has been uploaded. To access individual state reports, visit ````https://aspe.hhs.gov/sites/default/files/2021-08/StateBHCond-{State}.pdf```` The state name is in capital letters and if two words, is written without spaces or punctuation (example: NewYork, SouthDakota)
* The downloaded regulations were manually read and summarized in regulations.csv.

### Facility locations - within the facilities folder
* samhsa folder: Data from the SAMHSA Treatment Locator on May 25, 2022
    * 01-concat.ipynb: Stacks manually downloaded datasets from all states (these spreadsheets are located in the raw subfolder) to create a national dataset, which is samhsa-treatment-data.csv in the clean subfolder
    * 02-select-columns.ipynb: Selects the relevant columns and creates samhsa-treatment-data-subset-cols.csv in the clean subfolder
* carf folder: Data from the Commission on Accreditation of Rehabilitation Facilities on June 2, 2022
    * 01-carf-scrape.ipynb: Scrapes data from CARF - facility details, including addresses, are in carf-accredited-raw.csv and programs that the facilities actually offer are at programs-only-raw.csv. The program_offered column in the programs-only-raw.csv, which contained all programs offered, was then split out so that each program had its own column in programs-only-clean.csv.
    * 02-merge.ipynb: Merges facilities (carf-accredited-raw.csv) and programs (programs-only-clean.csv) files to create carf-accredited-merged.csv
    * 03-format-for-concat.ipynb: Creates and formats the dataset according to SAMHSA treatment locator data fields so the datasets can be concatenated later
* monte-nido folder: Data from Monte Nido and Affiliate's website as of June 3, 2022
    * Because SAMHSA and the Commission on Accreditation of Rehabilitation Facilities' data did not include Monte Nido facilities, I manually collected data from the website in monte-nido-raw.csv
    * 01-clean-and-concat.ipynb: Creates columns categorizing the programs available at each facility, following SAMHSA treatment locator data fields - this is saved into monte-nido-clean.csv. This data is then filtered to only contain facilities that offer residential treatment (As some Monte Nido facilities only offer outpatient treatment) and saved as monte-nido-for-concat.csv
* CONCAT-ALL folder: Concatenates all facilities from above folders into compiled-data.csv