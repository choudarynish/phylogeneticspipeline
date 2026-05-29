**Phylogenetic Tree Generation and Analysis Pipeline**

I'm gonna describe all the steps that I've performed to generate a phylogenetic tree here. I was asked to perform this for the **Septin protein**, found in the cytoskeleton of the cell.  Septins are a family of GTP-binding proteins associated with the cytoskeleton, originally discovered in budding yeast as essential for cytokinesis, and now known across fungi, animals, and some protists. They polymerise into filaments and higher-order structures (rings, gauzes) by assembling into hetero-oligomeric complexes. I am using septin protein sequences sampled across the major eukaryotic lineages to reconstruct how they are evolutionarily related — both within the family (the orthologous subgroups) and across kingdoms. 
I will be using the protein sequences of septins from each major organism classification to show the very reason we use a phylogenetic tree, i.e., to show how they are related.


**1. Data Retrieval**<br>
The protein sequences for septins from each organism were retrieved from NCBI

**Organisms selected:** Lab model organisms like *Mus musculus, C. elegans, Drosophila melanogaster*, and other standards like *Homo sapiens* and *S. cerevisiae*, also with a deep-branching lineage for rooting the tree using _Tetrahymena_.

**1.1 Data Selected for Analysis**<br>
KAI4039009.1 septin 2 [Homo sapiens]<br>
KAI4003248.1 septin 3 [Homo sapiens]<br>
AAN76547.1 septin 6 [Homo sapiens]<br>
KAI4013472.1 septin 7 [Homo sapiens]<br>
AAI38638.1 Septin 2 [Mus musculus]<br>
AAH55738.1 Septin 3 [Mus musculus]<br>
BAA08380.1 septin 6 [Mus musculus]<br>
AAH58587.1 Septin 7 [Mus musculus]<br>
NP_724659.1 peanut, isoform B [Drosophila melanogaster]<br>
NP_523430.1 septin 1 [Drosophila melanogaster]<br>
NP_001262764.1 septin 2, isoform B [Drosophila melanogaster]<br>
NP_724632.1 septin 5, isoform A [Drosophila melanogaster]<br>
NP_493388.1 Septin [Caenorhabditis elegans]<br>
QHB10463.1 Cdc3 [Saccharomyces cerevisiae]<br>
QHB07136.1 Cdc10 [Saccharomyces cerevisiae]<br>
CAA89604.1 CDC11 [Saccharomyces cerevisiae]<br>
QHB09098.1 Cdc12 [Saccharomyces cerevisiae]<br>
QHB07264.1 Shs1 [Saccharomyces cerevisiae]<br>
FAA14531.1 TPA: septin protein [Tetrahymena thermophila]<br>

I took one representative per subgroup per lineage wherever possible. For human and mouse I took one member of each of the four subgroups (septin 2, 3, 6, 7). For the invertebrates I took the septins they actually possess (only two or three subgroups are represented in invertebrates). For yeast I took all five core septins (Cdc3, Cdc10, Cdc11, Cdc12, Shs1), noting that fungal septins are not directly orthologous to the animal subgroups and are expected to form their own clade. 


**1.2 Procedure**<br>
* Go to [NCBI](https://www.ncbi.nlm.nih.gov/) and search for "Septins".
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/3d2335f7-0395-41cb-bfe1-69a28e536656" /><br>

* Filter results by Organism and Domain
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/0e32f2a8-2585-45a8-adfe-d871dd10aafb" /><br>

* Download the sequence in **FASTA format**. Repeat for all chosen organisms.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/3f2e57db-5d04-4c5e-b0a4-f8b6dbd3afb7" /><br>

* Save all sequences into a single `.txt` file and rename it to `seq.fasta`. 
* Clean the sequence identifier lines to show only the organism's name for better readability.
<br><img src="https://github.com/user-attachments/assets/5e5daeb6-1cc0-48e1-aad2-79054bae0d4e" width="800" alt="Editing Identifiers" /><br>



**2. Performing Multiple Sequence Alignment (MSA)**<br>
MSA aligns sequences based on shared similarities to highlight conserved regions and evolutionary changes.
For septins, the strongly conserved feature is the central GTP-binding (G) domain, which carries the P-loop (G1), and the G3 and G4 motifs. These regions align cleanly across all lineages and carry the phylogenetic signal.


**2.1 Tools Used**<br>
We are using the [MEGA Software](https://www.megasoftware.net/) for alignment and tree construction.

**2.2 Procedure**<br>
* Open MEGA and choose Align > Edit/Build Alignment.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/4111e99a-d8f3-4f83-8191-45f363d0abb6" /><br>


* Select Retrieve sequences from a file" and locate your `seq.fasta`.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/d85b248d-8a7f-4f48-b85e-759e38c58c78" /><br>


* Select all sequences and navigate to Alignment > Align by MUSCLE.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/57335b49-c059-4074-8c1b-a4a921f42394" /><br>


* Set the parameters (Gap Open −2.9, Gap Extend 0, Hydrophobicity Multiplier 1.2, Max Iterations 16, Clustering UPGMB) and click OK.
<br><img width="567" height="421" alt="image" src="https://github.com/user-attachments/assets/dbd53020-6494-403c-9fe5-450b39db9ea8" /><br>


* Export the alignment in MEGA format as `seqaligned.meg`, also in FASTA format as `seqaligned.fasta`.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/53ca7a90-27f3-4ffd-9375-638271d42643" /><br>
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/e5ad0487-ebc3-4a4b-97a0-358e8fc45acf" /><br>


**3 Data Cleaning and Trimming**<br>
We remove non-aligned regions (ragged N and C terminals) and excessive gaps that act as "noise" during tree generation. Removing them concentrates the analysis on the homologous, alignable core (the G-domain).
What the data showed: my raw alignment was 844 columns wide, but every sequence was 40–60% gaps. The well-occupied core (columns with ≥50% of sequences present) ran roughly from column 111 to 836; everything before 111 and after 836 was ragged terminal overhang, and the interior contained many sparse insertion columns. 

**3.1 Procedure:**<br>
1. In Alignment Explorer, identify columns with excessive gaps.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/a6a1bb37-f56e-466f-b5fb-6ff7d36aec50" /><br>
3. Highlight and Delete the unaligned ends (N-terminus and C-terminus).
4. Scan for unique large insertions that don't align with the alignment.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/ac37ccdc-d1d8-494c-a0bb-d96f9e6bc6de" /><br>
5. Export the trimmed alignment as FASTA and MEGA formats i.e, `seqtrimmed.fasta` and `seqtrimmed.meg`.

**4 Model Selection**<br>
Before building a Maximum Likelihood tree, the best-fit amino-acid substitution model must be chosen, because ML estimates the tree under an explicit model of how residues change. Skipping this and using a raw distance would discard that information.

**4.1 Procedure**<br>

1. Main MEGA window → Models → Find Best Protein Models (ML) → load `seqtrimmed.meg`.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/e72ea892-108c-4690-a526-a2f9dd0d8176" /><br>
<br><img width="620" height="593" alt="image" src="https://github.com/user-attachments/assets/0097739d-2866-4b71-96ea-f3f963805898" /><br>
2. MEGA ranks models by BIC and AICc. Choose the model with the lowest BIC.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/32eae2f3-2fe9-4f75-96b2-829830520899" /><br>
4. Record the winner and its parameters (for septins this is typically LG+G or LG+G+I)


**5. Constructing the Phylogenetic Tree**<br>
This is the final core step to visualize evolutionary relationships.
I built a Maximum Likelihood (ML) tree, which finds the topology that makes the observed alignment most probable under the chosen substitution model. ML is preferred over distance methods like Neighbor-Joining for deep, divergent datasets like this one because it models site-by-site substitution rather than collapsing everything to a single distance.

**5.1 Procedure**<br>
1. Return to the main MEGA window and click Phylogeny > Construct/Test Maximum Likelihood Tree.
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/012c5271-e2bc-4219-83f3-c6a28ae01a50" /><br>
3. Load your `seqaligned.meg` file.
4. In Analysis Preferences, set the following:
   Substitution model: the best-fit model from section 4, i.e., LG Model
   Rates among sites: Gamma (G), 5 categories
   Gaps/Missing data: Partial deletion, Site Coverage Cutoff 95%
   ML Heuristic: Nearest-Neighbor-Interchange (NNI)
   Test of Phylogeny: Adaptive Bootstrap, Threshold of 5.00
 <br><img width="620" height="789" alt="image" src="https://github.com/user-attachments/assets/19aff01b-b8e6-401a-a1b3-0c967f03bf39" /><br>
5. Click OK to generate and visualize the final tree.
<br><img width="472" height="379" alt="image" src="https://github.com/user-attachments/assets/9997a8a2-651c-4c4c-91fb-4b0a42dfb8cb" /><br>
6. Open the tree in the in-built tree viewer
<br><img width="1920" height="1026" alt="image" src="https://github.com/user-attachments/assets/f328bb06-4c58-4bca-ae01-376a63bf4730" /><br>
7. Toggle options to view ancestors, node lengths, etc.
8. Export the tree in Newick format and as an image

**5. Interpretation and Analysis**<br>
After the phylogenetic tree is generated, we are interested to analyse the tree for what it would like to infer.
_Tetrahymena thermophila_, falls at the base on a very long branch (0.882, the longest in the tree), which is what was expected — it is the most distantly related organism in the set and serves as a natural outgroup to root the tree.
The fungal septins form their own clade, separate from the animal septins. The _Saccharomyces_ sequences (Cdc3, Cdc10, Cdc11, Cdc12, Shs1) do not nest inside the animal groups. CDC11 and SHS1 group together with strong support (bootstrap 95), and the other Cdc proteins branch away from the animal subgroups. This matches the known biology: although all septins descend from a single ancient ancestor, the fungal and animal septins are not directly orthologous — the duplications that produced yeast's five core septins happened independently of the duplications that produced the animal subgroups. So "yeast Cdc10" is not the ortholog of any one human septin; it is a fungal-lineage paralog. 
Orthologs group by gene identity across species, not by organism — which validates the balanced sampling. The clearest signal in the tree is the tight, maximally-supported ortholog pairs: S7_MusMusculus with S7_Drosophila (bootstrap 100), S3_HomoSapiens with S3_MusMusculus (100), S2/S6_MusMusculus with S2_HomoSapiens (100). Mouse septin 7 sits with fly septin 7, not with mouse septin 2. This is the signature of a clean phylogeny: when the same gene from different species groups together rather than different genes from the same species, the tree is tracking gene ancestry (orthology), which is what we want. Had I pooled all paralogs without balancing, these clean ortholog signals would have been buried under lineage-specific expansion.
The septin subgroups are partially recovered. The SEPT7-type sequences group together, and the SEPT3-type sequences (S3_HomoSapiens + S3_MusMusculus) form a strong clade sitting near the fungal group. This is consistent with the four-subgroup model of animal septins, and with the observation that only a subset of subgroups is represented in invertebrates.

