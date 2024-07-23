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
## 1. Use the data set we provide
### 1.1 Cross verification
If you use our dataset for cross-validation, all you need to do is enter the following command in the termi

    python main.py 
    
### 1.2 Modify model parameters 
You just need to adjust the following code in the main.py file.

    if __name__ == "__main__":
        drug_atc_path = 'data/drug_ATC/second_ATC.csv'
        atc_target_protein_path = 'data/ATC_target_protein/second_uniprot.csv'
        atc_side_effects_path = 'data/ATC_side_effects/second_side_effects.csv'
        atc_fingerprint_path = 'data/ATC_fingerprint/second_fingerprint.csv'
        op = Options(drug_atc_path, atc_target_protein_path, atc_side_effects_path, atc_fingerprint_path, level=4, omega=0.9)
        op.train(k=10)
          
+ drug_atc_path is the file path storing the adjacency matrix of drug and ATC codes.
+ atc_target_protein_path is the file path storing the adjacency matrix of ATC codes and target protein.
+ atc_side_effects_path is the file path storing the adjacency matrix of ATC codes and side effects.
+ atc_fingerprint_path is the file path storing the adjacency matrix of ATC codes and fingerprint.
+ The parameter level represents the level of ATC codes. It can be 2, 3 and 4.
+ The parameter omega represents parameter in WKNKN when reformulating the adjacency matrix. It can be any numbers between 0.0 and 1.0.
+ The parameter k represents the number of folds in cross-validation. k was set to 10 in our study.
## 2. Use your own data set
### 2.1 Preprocessed data set
You need to prepare some files, which are all in CSV format. The detailed format is displayed as below:
#### 1. The adjacency matrix of drug-ATC code associations
#### 2. Drug fingerprints matrix
#### 3. Drug side effects matrix
#### 4. Drug target proteins matrix
#### 5. Drug interaction kernel
#### 6. Because it involves ATC code tree structure to find the shortest path, different data sets involve different ATC, so you should prepare the shortest path file for ATC codes at different levels. It is also in CSV format, as shown below

