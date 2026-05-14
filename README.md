# phylogeneticspipeline
**Phylogenetic Tree Generation and Analysis**

I'm gonna describe all the steps that I've performed to generate a phylogenetic tree here
I was asked to perfrom this for the septin protein, found in the cytoskeleton of the cell
I will be using the protein sequences of septins from each major organism classification to show the very reason we use a phylogenetic tree, i.e. to show how they are related


**1. Data Retrieval**<br>
The protein sequences for septins from each organism was retrieved from UniProt Protein Data Bank (PDB)
We will try to choose the sequences which are highly conserved, because it makes sense to draw evolutionary significance from the results, the literature states that the GTPase domain is the highly conserved one.
The choice of organisms are the lab model organisms, like _Mus musculus, C.elegans, Drosophila melanogasster, etc._, and other standards like _Homo sapiens, S. cerevisiae_ and others

  1.1 Data Retrieved for Analysis<br>
  Here is what I have chosen for the tree generation, based on what I have considered in the main section:
   >sp|Q8WYJ6|SEPT1_HUMAN Septin-1 OS=Homo sapiens OX=9606 GN=SEPTIN1 PE=1 SV=3<br>
   >sp|Q5EB96|SEPT1_RAT Septin-1 OS=Rattus norvegicus OX=10116 GN=Septin1 PE=1 SV=1<br>
   >sp|A5PJU9|SEPT1_BOVIN Septin-1 OS=Bos taurus OX=9913 GN=SEPTIN1 PE=2 SV=1<br>
   >sp|Q5ZMH1|SEPT2_CHICK Septin-2 OS=Gallus gallus OX=9031 GN=SEPTIN2 PE=2 SV=1<br>
   >sp|Q9DE33|SEP2A_XENLA Septin-2A OS=Xenopus laevis OX=8355 GN=sept2-a PE=1 SV=1<br>
   >sp|P42207|SEPT1_DROME Septin-1 OS=Drosophila melanogaster OX=7227 GN=Septin1 PE=1 SV=1<br>
   >tr|Q9U334|Q9U334_CAEEL Septin OS=Caenorhabditis elegans OX=6239 GN=unc-59 PE=1 SV=1<br>

  1.2 Procedure<br>
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
 <img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/2afb9dc0-6b74-45a1-95d4-f2bd78662b56" />
<br>


**2. Performing MSA(Multiple Sequence Alignment)**
The sequences retrieved from the biological databases are aligned to each other based on the similar sequences they share, which is demonstrated by MSA 

2.1 Tools Used<br>
We will be using the MEGA Software for performing the MSA

2.2 Procedure<br>
Install the MEGA application https://www.megasoftware.net/ 

Open the application to get the welcome screen
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/4b1f7c63-6025-4886-9474-a5ed68e67957" /><br>

Choose Align> Edit/Build Alignment
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/6517d606-407b-4383-8cdb-dd41bac49f7d" /><br>

Choose to retrieve sequences from the file
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/03cc23a9-6808-427b-8b06-5b123446f0bc" /><br>

Loacte the file in the dialog box which will pop up

The application shows the sequences from the file, coded by a unique colour for each amino acid residue
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/761b7118-9c82-4a37-81c6-94f89c4f255a" ><br>

Select all the sequences by using keyboard shortcuts or just the cursor
Now go to Alignment > Align by MUSCLE
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/c3ab478a-20f9-4bbe-bcde-ef4e106bd8ac" /><br>

Change the parameters as follows:, if required and click OK

<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/f6d78fdc-bed9-4e23-89ed-ca499a3ccd72" /><br>

The application returns the aligned sequences onto it
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/9f20520c-c35d-478f-beb8-6e1c8c9e9c04" /><br>

Export the alignment in the MEGA format as shown, after which a dialog box pops up to save it. Save it in the same folder as the previous one, as sequencesaligned.meg
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/b4b024e9-b67a-4ea7-94da-6bbea3d974fc" /><br>

This format is used to further analyse it within the same application, reducing the dependence on multiple applications.

By the end of this step, we must get the sequences underwent MSA, thus generating sequencesaligned.meg
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/d87d7262-54a0-4fe5-9c7c-f08c8ce74560" />

Why are we using MUSCLE here? What parameteres did we change? Logic behind it?<br>
**2.3 Data cleaning and processing**







  



 



