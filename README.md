# Molecule-Recommendation

## Links
- [Website](https://yaruyang.wixsite.com/mol-rec)
- [Video](https://www.youtube.com/watch?v=R2_QVLiIKYo&t=5s)
- [Summary Report](https://83b66dc9-0e7e-4155-9b49-600d07b0c53e.filesusr.com/ugd/609a2c_1855f7a0acc042929e761885a86e515f.pdf)

## Project Overview
The research Project aims to design and implement a hybrid chemical recommender system. This system will leverage a combination of algorithms, including collaborative filtering, content-based approaches, Graph Neural Networks (GNNs), and autoencoders to effectively identify and recommend compounds of interest. It focuses on introducing scientific researchers to potentially unknown chemical compounds within large-scale chemical datasets, enhancing discovery and research efficiency in chemistry and related fields.

## Methodology
![Methodology](https://github.com/PragatiNaikare311/Molecule-Recommendation/assets/143132647/acc069ff-6a93-4078-963a-6a7440a75289)

The system leverages users’ past research experiences to recommend innovative synthesized molecules. These recommendations will serve as potential subjects of investigation for researchers in biomedical, drug, and chemistry-related fields. To achieve this, we have developed a powerful molecule recommendation pipeline, tailored to recommend molecules to researchers based on their past interactions. 

### 2-Stage Recommendation Pipeline
Given a researcher’s historical molecule interactions, our recommendation pipeline curates a set of molecules from the MolRec data and generates novel molecules aligned with the researcher’s interests.

#### Stage I - Classical Recommendation
In the first stage, we use state-of-the-art methods for recommendations from the MolRec dataset based on collaborative filtering and chemical semantic similarity [Barros et al., 2021]. Our results show that a hybrid of alternating least squares and chemical semantic similarity based on the molecule’s ChEBI ontology give the best performance on a held-out test set.

Results: <img width="1457" alt="Screenshot 2024-05-04 at 11 05 05 AM" src="https://github.com/PragatiNaikare311/Molecule-Recommendation/assets/143132647/ef02b347-f2bb-41ba-bd03-49547d907a43">
<img width="1434" alt="Screenshot 2024-05-04 at 11 04 50 AM" src="https://github.com/PragatiNaikare311/Molecule-Recommendation/assets/143132647/5ef0caef-fd6c-4fa5-89ab-8df2c66b13e3">

#### Stage II - Deep Generative Model
In the second stage, we train a Junction Tree Variational Autoencoder [Jin et al., 2018] on the Zinc250K dataset [Sterling and Irwin, 2015] of 250K drug-like compounds. We are then able to condition generations from the VAE on the molecules recommended in the first stage to generate novel molecules beyond those in the MolRec data based on the researcher’s interests.
