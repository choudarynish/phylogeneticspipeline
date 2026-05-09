# phylogeneticspipeline
**Phylogenetic Tree Generation and Analysis**

I'm gonna describe all the steps that I've performed to generate a phylogenetic tree here

So I was asked to perfrom this for the septin protein, found in the cytoskeleton of the cell
I will using the protein sequences of septins from each major classification to show the very reason we use a phylogenetic tree , to show how they are related



**1. Data Retrieval**
The protein sequences for septins from each organism was retrieved from UniProt Protein Data Bank (PDB)
We will try to choose the sequences which are highly conserved, because it makes sense to draw evolutionary significance from the results, the literature states that the GTPase domain is the highly conserved one.
The choice of organisms are the lab model organisms, like _Mus musculus, C.elegans, Drosophila melanogasster, etc._

  1.1 Data Retrieved for Analysis
  Here is what I have chosen for the tree generation, based on what I have considered in the main section:
   >sp|Q8WYJ6|SEPT1_HUMAN Septin-1 OS=Homo sapiens OX=9606 GN=SEPTIN1 PE=1 SV=3<br>
   >sp|Q5EB96|SEPT1_RAT Septin-1 OS=Rattus norvegicus OX=10116 GN=Septin1 PE=1 SV=1<br>
   >sp|A5PJU9|SEPT1_BOVIN Septin-1 OS=Bos taurus OX=9913 GN=SEPTIN1 PE=2 SV=1<br>
   >sp|Q5ZMH1|SEPT2_CHICK Septin-2 OS=Gallus gallus OX=9031 GN=SEPTIN2 PE=2 SV=1<br>
   >sp|Q9DE33|SEP2A_XENLA Septin-2A OS=Xenopus laevis OX=8355 GN=sept2-a PE=1 SV=1<br>
   >sp|P42207|SEPT1_DROME Septin-1 OS=Drosophila melanogaster OX=7227 GN=Septin1 PE=1 SV=1<br>
   >tr|Q9U334|Q9U334_CAEEL Septin OS=Caenorhabditis elegans OX=6239 GN=unc-59 PE=1 SV=1<br>

  1.2 Procedure
  Go to UniProt https://www.uniprot.org/
  In the Search tab, search for "Septins" and proceed
  <img src="https://github.com/user-attachments/assets/2864427d-b749-4c02-9b78-6309bd0de42c" width="700" alt="UniProt Search Results" /><br>
  
  Filter the search results for choosing the organism and the domain
  <img src="https://github.com/user-attachments/assets/153ba1fe-3d6b-4e9c-9d27-1628372de553" width="700" alt="Filtering by Organism and Domain" /><br>
  
  After choosing the relevant query result, proceed to download the sequence in the FASTA format
  <img src="https://github.com/user-attachments/assets/64b42318-fae6-40d0-873a-ed6608ad10b2" width="700" alt="Downloading FASTA format" /><br>
  
  Proceed with all other organisms as the same mentioned above
  
  Copy the FASTA sequenences into a new .txt file annd rename it to sequences.fasta and paste them there
  
  Edit the sequence identifier line as the organism name or the PDB ID
  <img src="https://github.com/user-attachments/assets/5e5daeb6-1cc0-48e1-aad2-79054bae0d4e" width="700" alt="Editing Sequence Identifiers" /><br>

  By the end of this step, you must have a file that contais all the retrieved sequences in one file, i.e, sequences.fasta
  <img src="https://github.com/user-attachments/assets/86adb0c5-c148-48a5-8e35-ca55491eb4dc" width="700" alt="Final Sequences File" /><br>

  



 



