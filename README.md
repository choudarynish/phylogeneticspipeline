# **Phylogenetic Tree Generation and Analysis Pipeline**

I'm gonna describe all the steps that I've performed to generate a phylogenetic tree here. I was asked to perform this for the **Septin protein**, found in the cytoskeleton of the cell. I will be using the protein sequences of septins from each major organism classification to show the very reason we use a phylogenetic tree, i.e., to show how they are related.

---

## **1. Data Retrieval**
The protein sequences for septins from each organism were retrieved from the **UniProt Protein Data Bank (PDB)**. We choose sequences that are highly conserved to ensure evolutionary significance; literature states that the **GTPase domain** is the highly conserved region in septins. 

**Organisms selected:** Lab model organisms like *Mus musculus, C. elegans, Drosophila melanogaster*, and other standards like *Homo sapiens* and *S. cerevisiae*.

### **1.1 Data Selected for Analysis**
> sp|Q8WYJ6|SEPT1_HUMAN Septin-1 OS=Homo sapiens OX=9606 GN=SEPTIN1 PE=1 SV=3
> sp|Q5EB96|SEPT1_RAT Septin-1 OS=Rattus norvegicus OX=10116 GN=Septin1 PE=1 SV=1
> sp|A5PJU9|SEPT1_BOVIN Septin-1 OS=Bos taurus OX=9913 GN=SEPTIN1 PE=2 SV=1
> sp|Q5ZMH1|SEPT2_CHICK Septin-2 OS=Gallus gallus OX=9031 GN=SEPTIN2 PE=2 SV=1
> sp|Q9DE33|SEP2A_XENLA Septin-2A OS=Xenopus laevis OX=8355 GN=sept2-a PE=1 SV=1
> sp|P42207|SEPT1_DROME Septin-1 OS=Drosophila melanogaster OX=7227 GN=Septin1 PE=1 SV=1
> tr|Q9U334|Q9U334_CAEEL Septin OS=Caenorhabditis elegans OX=6239 GN=unc-59 PE=1 SV=1

### **1.2 The Procedure**
* **Step 1:** Go to [UniProt](https://www.uniprot.org/) and search for "Septins".
<img src="https://github.com/user-attachments/assets/2864427d-b749-4c02-9b78-6309bd0de42c" width="800" alt="UniProt Search Results" />

* **Step 2:** Filter results by **Organism** and **Domain** to find high-quality reviewed entries.
<img src="https://github.com/user-attachments/assets/153ba1fe-3d6b-4e9c-9d27-1628372de553" width="800" alt="Filtering" />

* **Step 3:** Download the sequence in **FASTA format**. Repeat for all chosen organisms.
<img src="https://github.com/user-attachments/assets/64b42318-fae6-40d0-873a-ed6608ad10b2" width="800" alt="FASTA Download" />

* **Step 4:** Consolidate all sequences into a single `.txt` file and rename it to `sequences.fasta`. 
* **Step 5:** Clean the sequence identifier lines to show only the Organism name or PDB ID for better readability later.
<img src="https://github.com/user-attachments/assets/5e5daeb6-1cc0-48e1-aad2-79054bae0d4e" width="800" alt="Editing Identifiers" />

---

## **2. Performing Multiple Sequence Alignment (MSA)**
MSA aligns sequences based on shared similarities to highlight conserved regions and evolutionary changes.

### **2.1 Tools Used**
We are using the [MEGA Software](https://www.megasoftware.net/) for alignment and tree construction.

### **2.2 The Procedure**
* **Step 1:** Open MEGA and choose **Align > Edit/Build Alignment**.
<img width="1440" height="900" alt="MEGA Welcome" src="https://github.com/user-attachments/assets/4b1f7c63-6025-4886-9474-a5ed68e67957" />

* **Step 2:** Select **"Retrieve sequences from a file"** and locate your `sequences.fasta`.
<img width="1440" height="900" alt="Load File" src="https://github.com/user-attachments/assets/03cc23a9-6808-427b-8b06-5b123446f0bc" />

* **Step 3:** Select all sequences and navigate to **Alignment > Align by MUSCLE**.
<img width="1440" height="900" alt="Align by MUSCLE" src="https://github.com/user-attachments/assets/c3ab478a-20f9-4bbe-bcde-ef4e106bd8ac" />

* **Step 4:** Set **Gap Penalties** (Open: -2.9, Extend: 0) and click OK.
<img width="1440" height="900" alt="Parameters" src="https://github.com/user-attachments/assets/f6d78fdc-bed9-4e23-89ed-ca499a3ccd72" />

* **Step 5:** **Export** the alignment in **MEGA format** as `sequencesaligned.meg`.
<img width="1440" height="900" alt="Export MEGA" src="https://github.com/user-attachments/assets/b4b024e9-b67a-4ea7-94da-6bbea3d974fc" />

---

### **2.3 Data Cleaning and Trimming**
We remove non-aligned regions (ragged N and C terminals) and excessive gaps that act as "noise" during tree generation.

**The Procedure:**
1. In **Alignment Explorer**, identify columns with excessive gaps.
2. **Highlight** and **Delete** the unaligned ends (N-terminus and C-terminus).
3. Scan for unique large insertions that don't align with the consensus and consider removing them to improve signal-to-noise ratio.

---

## **3. Constructing the Phylogenetic Tree**
This is the final core step to visualize evolutionary relationships.

### **3.1 Procedure**
* **Step 1:** Return to the main MEGA window and click **Phylogeny > Construct/Test Neighbor-Joining Tree**.
* **Step 2:** Load your `sequencesaligned.meg` file.
* **Step 3:** In **Analysis Preferences**, set the following:
    * **Test of Phylogeny:** Bootstrap method (1000 replications).
    * **Model/Method:** p-distance (for Protein).
* **Step 4:** Click OK to generate and visualize the final tree.

**Logic: Why Bootstrap 1000?**
The Bootstrap value shows the confidence level of a branch. Running 1000 iterations checks how often a grouping occurs; values >70 generally indicate a reliable evolutionary relationship.
