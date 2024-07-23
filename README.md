# Requirements
+ python = 3.10
+ cvxopt = 1.3.2
+ ecos = 2.0.12
+ numpy+mkl = 1.26.2
+ osqp = 0.6.3
+ pandas = 1.3.4
+ scikit-learn = 1.3.2
+ scipy = 1.11.3
+ scs = 3.2.3
# Files:
 filename | explain
 ------------------------- | -------------------------
 drug_ATC | The adjacency matrix of drugs and ATC codes at the second,third,fourth level.
 drug_fingerprint | The drug representation based on their fingerprints.
 drug_side_effects | The drug representation based on their side effects.
 drug_target_protein | The drug representation based on their target proteins.
 drug_interaction | The drug kernel using the interaction information collected in STITCH.
 ATC_fingerprint | The ATC code representation based on their fingerprints at the second,third,fourth level.
 ATC_side_effects | The ATC code representation based on their side effects at the second,third,fourth level.
 ATC_target_protein | The ATC code representation based on their target proteins at the second,third,fourth level.

Drug SMILES information, drug ATC code information, and drug target protein information were obtained from DrugBank database (https://go.drugbank.com/), drug side effect information were obtained from SIDER database (http://sideeffects.emblde/), and drug interaction information was obtained from STITCH website (http://stitch4.embl.de/).
# Usage
## How to use it?
### 1. Use the data set we provide
#### 1.1 Cross verification
If you use our dataset for cross-validation, all you need to do is enter the following command in the termi

     python main.py 

