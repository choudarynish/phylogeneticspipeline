# **Phylogenetic Tree Generation and Analysis Pipeline**

I'm gonna describe all the steps that I've performed to generate a phylogenetic tree here. I was asked to perform this for the **Septin protein**, found in the cytoskeleton of the cell. I will be using the protein sequences of septins from each major organism classification to show the very reason we use a phylogenetic tree, i.e., to show how they are related.

---

## **1. Data Retrieval**
The protein sequences for septins from each organism were retrieved from NCBI

**Organisms selected:** Lab model organisms like *Mus musculus, C. elegans, Drosophila melanogaster*, and other standards like *Homo sapiens* and *S. cerevisiae*.

### **1.1 Data Selected for Analysis**
> sp|Q8WYJ6|SEPT1_HUMAN Septin-1 OS=Homo sapiens OX=9606 GN=SEPTIN1 PE=1 SV=3
> sp|Q5EB96|SEPT1_RAT Septin-1 OS=Rattus norvegicus OX=10116 GN=Septin1 PE=1 SV=1
> sp|A5PJU9|SEPT1_BOVIN Septin-1 OS=Bos taurus OX=9913 GN=SEPTIN1 PE=2 SV=1
> sp|Q5ZMH1|SEPT2_CHICK Septin-2 OS=Gallus gallus OX=9031 GN=SEPTIN2 PE=2 SV=1
> sp|Q9DE33|SEP2A_XENLA Septin-2A OS=Xenopus laevis OX=8355 GN=sept2-a PE=1 SV=1
> sp|P42207|SEPT1_DROME Septin-1 OS=Drosophila melanogaster OX=7227 GN=Septin1 PE=1 SV=1
> tr|Q9U334|Q9U334_CAEEL Septin OS=Caenorhabditis elegans OX=6239 GN=unc-59 PE=1 SV=1 chang theseeeeeeee

### **1.2 The Procedure**
* Go to [NCBI](https://www.ncbi.nlm.nih.gov/) and search for "Septins".
<img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/3d2335f7-0395-41cb-bfe1-69a28e536656" />

* Filter results by Organism and Domain
<img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/0e32f2a8-2585-45a8-adfe-d871dd10aafb" />

* Download the sequence in **FASTA format**. Repeat for all chosen organisms.
<img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/3f2e57db-5d04-4c5e-b0a4-f8b6dbd3afb7" />

* Save all sequences into a single `.txt` file and rename it to `seq.fasta`. 
* Clean the sequence identifier lines to show only the organism's name for better readability.
<img src="https://github.com/user-attachments/assets/5e5daeb6-1cc0-48e1-aad2-79054bae0d4e" width="800" alt="Editing Identifiers" />

---

## **2. Performing Multiple Sequence Alignment (MSA)**
MSA aligns sequences based on shared similarities to highlight conserved regions and evolutionary changes.

### **2.1 Tools Used**
We are using the [MEGA Software](https://www.megasoftware.net/) for alignment and tree construction.

### **2.2 The Procedure**
* Open MEGA and choose Align > Edit/Build Alignment.
<img width="1440" height="900" alt="MEGA Welcome" src="https://github.com/user-attachments/assets/4b1f7c63-6025-4886-9474-a5ed68e67957" />

* Select Retrieve sequences from a file" and locate your `seq.fasta`.
<img width="1440" height="900" alt="Load File" src="https://github.com/user-attachments/assets/03cc23a9-6808-427b-8b06-5b123446f0bc" />

* Select all sequences and navigate to Alignment > Align by MUSCLE.
<img width="1440" height="900" alt="Align by MUSCLE" src="https://github.com/user-attachments/assets/c3ab478a-20f9-4bbe-bcde-ef4e106bd8ac" />

* Set Gap Penalties (Open: -2.9, Extend: 0) and click OK.
<img width="1440" height="900" alt="Parameters" src="https://github.com/user-attachments/assets/f6d78fdc-bed9-4e23-89ed-ca499a3ccd72" />

* Export the alignment in MEGA format*as `seqaligned.meg`.
<img width="1440" height="900" alt="Export MEGA" src="https://github.com/user-attachments/assets/b4b024e9-b67a-4ea7-94da-6bbea3d974fc" />

---

### **3 Data Cleaning and Trimming**
We remove non-aligned regions (ragged N and C terminals) and excessive gaps that act as "noise" during tree generation.

**3.1 Procedure:**
1. In Alignment Explorer, identify columns with excessive gaps.
2. Highlight and Delete the unaligned ends (N-terminus and C-terminus).
3. Scan for unique large insertions that don't align with the alignment.

---

## **4. Constructing the Phylogenetic Tree**
This is the final core step to visualize evolutionary relationships.

### **4.1 Procedure**
* Return to the main MEGA window and click Phylogeny > Construct/Test Neighbor-Joining Tree.
* Load your `seqaligned.meg` file.
* In Analysis Preferences, set the following:
    * Test of Phylogeny: Bootstrap method (1000 replications).
    * Model/Method: p-distance (for Protein).
*  Click OK to generate and visualize the final tree.

**Logic: Why Bootstrap 1000?**
The Bootstrap value shows the confidence level of a branch. Running 1000 iterations checks how often a grouping occurs; values >70 generally indicate a reliable evolutionary relationship.
