# Transcribe SFRC tables with Mistral AI

Example Python code to transcribe tables from regulatory filings into a digital form. To run these examples you will need an [Anaconda environment](https://www.anaconda.com/), a Mistral [API key](https://docs.mistral.ai/getting-started/quickstart/).
In this example we transcribed the balance sheet table from Solvency and Financial Conditions reports that companies need to file every year.

For a subset we took the main 18 life insurance companies operating on the Italian market.

## Companies in scope

 - Credemvita S.p.A.
 - AXA MPS Assicurazioni Vita
 - CRÈDIT AGRICOLE VITA
 - Società Reale Mutua di Assicurazioni
 - Cardif Vita S.p.A.
 - MEDIOLANUM VITA S.p.A.
 - Generali Italia S.p.A.
 - Banco BPM Vita S.p.A.
 - HDI ASSICURAZIONI S.p.A.
 - Gruppo Assicurativo Poste Vita
 - FIDEURAM VITA S.P.A.
 - CNP Vita Assicura S.p.A.
 - ITAS VITA
 - Helvetia Vita S.p.A.
 - Vittoria Assicurazioni S.p.A.
 - GROUPAMA ASSICURAZIONI S.P.A.
 - UniCredit Allianz Vita S.p.A.
 - Zurich Investments Life S.p.A.

## Description of the process

The process of extraction is performed in 5 phases.

### Phase 1: Find the reports and identify the relevant tables (manually). 
 1) Identify the new SFCR report and save it into the folder Input.
 2) Identify the pages where the tables of interest are.
 3) Compile the map of the company run in the master_list.csv.

### Phase 2: Run the Extraction notebook (released on 23-September-2025). 
The notebook performs the following steps (with slight modifications depending on the table format):
 1) Save the page with the table into a separate folder Single_pdf.
 2) Use either a Python package or specialized LLM to create a digital equivalent of the table.
 3) Fix the systemic errors that prevent the table from being saved as DataFrame.
 4) Save the DataFrame into the Output folder.

### Phase 3: Run the Processing notebook. 
The notebook applies fixes to the DataFrame to make the numbers closer to the reported numbers. It joins all the tables into a single dataset. 

### Phase 4: Run the Cross-Validation notebook. 
The notebook applies a series of tests that check for the internal consistency between the numbers. Flags the potential errors.

## Contact
A version of this process is used by OSM to extract data for our actuarial models. One of the benefits of releasing our code is the feedback and improvement ideas. If you have any, you can contact us at gregor@osmodelling.com.

## License
MIT license

### Phase 5: Final modifications to the table and a manual inspection. 

