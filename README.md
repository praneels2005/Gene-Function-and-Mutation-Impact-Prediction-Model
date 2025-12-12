This project implements an end-to-end bioinformatics and machine learning pipeline for classifying gene function and predicting mutation impact using engineered features derived from mRNA sequence records. The system consists of three major components: data acquisition, machine learning modeling, and visualization/interpretation.
Follow the execution order below to reproduce the full workflow.

Before executing the pipeline...

Create a virtual environment: python3 -m venv venv

Activate the environment: source venv/bin/activate

Install the reqiurements: pip install -r requirements.txt

Now, execute the pipeline from the root directory:

1. Data Pipeline — Data_Pipeline.ipynb

This notebook retrieves mRNA sequence records from NCBI GenBank using the Entrez E-utilities API and performs structured feature engineering.
When executed, it automatically:

Downloads raw GenBank records into the raw_data/ directory

Extracts mRNA, CDS, and amino-acid FASTA files into the sequences/ directory

Computes nucleotide composition, amino-acid composition, CDS metrics, k-mer frequencies, and other biologically relevant features

Produces a complete dataset titled cleaned_features.csv

⚠️ Important:
cleaned_features.csv is required for all downstream notebooks.
The raw_data/ and sequences/ folders will update automatically whenever the pipeline is re-run.

2. Machine Learning Pipeline — ML_Engineer.ipynb

This notebook trains multiple models for gene function classification and builds the mutation-impact prediction framework.
It performs:

Train/test splits and feature scaling

Training and evaluation of Logistic Regression, Gaussian Naive Bayes, and Random Forest

Selection of the best model (Random Forest)

Export of a packaged model bundle containing:
- the trained Random Forest classifier
- the fitted scaler
- the ordered feature list

Generation of synthetic mutation data for impact prediction

Feature importance and interpretability analysis

Running this notebook updates the models/ directory with all serialized model artifacts.

3. Visualization & Interpretation — Visualization.ipynb

This final notebook generates all publication-quality figures and analyses used to validate the modeling pipeline.
It includes:

PCA projections to visualize gene separability

Pairwise feature relationships

Confusion matrices and performance visualizations

Mutation-impact distributions

Random Forest feature importance plots

Other exploratory analyses supporting the results in the final report

These visualizations serve as the foundation for our interpretive claims and final conclusions.

**b** Summary **b**

Executing these three notebooks in order:

1. Builds the dataset

2. Trains and packages the best gene-classification and mutation-impact models

3. Generates all visualizations used for reporting and evaluation