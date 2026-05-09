# phylogeneticspipeline
**Phylogenetic Tree Generation and Analysis **

I'm gonna describe all the steps that I've performed to generate a phylogenetic tree here

So I was asked to perfrom this for the septin protein, found in the cytoskeleton of the cell
I will using the protein sequences of septins from each major classification to show the very reason we use a phylogenetic tree , to show how they are related



**1. Data Retrieval**
The protein sequences for septins from each organism was retrieved from UniProt Protein Data Bank (PDB)
We will try to choose the sequences which are highly conserved, because it makes sense to draw evolutionary significance from the results, the literature states that the GTPase domain is the highly conserved one.
The choice of organisms are the lab model organisms, like _Mus musculus, C.elegans, Drosophila melanogasster, etc._

  1.1 Data Retrieved for Analysis
  Here is what I have chosen for the tree generation, based on what I have considered in the main section:


  1.2 Procedure
  Go to UniProt https://www.uniprot.org/
  In the Search tab, search for "Septins" and proceed
  <img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/2864427d-b749-4c02-9b78-6309bd0de42c" />
  Filter the search results for choosing the organism and the domain
  <img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/153ba1fe-3d6b-4e9c-9d27-1628372de553" />
  After choosing the relevant query result, proceed to download the sequence in the FASTA format
  <img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/64b42318-fae6-40d0-873a-ed6608ad10b2" />
  Proceed with all other organisms as the same mentioned above
  Copy the FASTA sequenences into a new .txt file annd rename it to Sequences.fasta and paste them there
  Edit the sequence identifier line as the organism name or the PDB ID
  <img width="1919" height="1027" alt="image" src="https://github.com/user-attachments/assets/5e5daeb6-1cc0-48e1-aad2-79054bae0d4e" />



