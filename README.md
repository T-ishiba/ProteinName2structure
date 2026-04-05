# ProteinName2structure
# Structural Biology Tools: PDB Metadata Fetcher & Sequence Coverage Mapper

A collection of Python scripts designed to streamline structural biology workflows and bioinformatics data collection. These tools automate the retrieval of macromolecular structural data from the Protein Data Bank (PDB), extract deeply nested metadata, and visualize sequence coverage for complex protein analyses.

## 🛠️ Tools Included

### 1. PDB Metadata Fetcher (`pdb_metadata_extractor.ipynb`)
A robust script that automatically retrieves relevant PDB IDs based on a UniProt search query and bulk-downloads structural data in the latest mmCIF format. It simultaneously extracts key metadata from each structure and generates a TSV-formatted database suitable for analysis in Excel or other spreadsheet software.

**Features:**
- **UniProt API Integration:** Comprehensively retrieves PDB IDs using protein names and species (e.g., `BRD9&&human`).
- **Bulk mmCIF Download:** Saves structures locally in the latest standard format (`.cif`), fully supporting large macromolecular complexes (e.g., Cryo-EM structures).
- **Advanced Metadata Extraction:** Utilizes Biopython's `MMCIF2Dict` to parse and output the following information to a TSV file:
  - `PDB_ID`, `Title`, `Method`, `Resolution`, `DOI`
  - `Date`: Initial Deposition Date to the PDB, allowing chronological sorting of structural data.
  - `Organism`: Accurately integrates both natural and genetically engineered source organisms.
  - `Proteins`: Protein subunits composing the complex (automatically filters out water molecules).
  - `Ligands`: Bound small-molecule ligands and inhibitors (automatically filters out water molecules).

### 2. Sequence Coverage Mapper (`sequence_coverage_mapper.ipynb`)
A visualization tool that performs local alignments between a user-defined full-length reference sequence and a local directory of mmCIF files. It generates a high-resolution, amino-acid-level coverage map.

**Features:**
- **Automated Local Alignment:** Uses Biopython's `PairwiseAligner` to quickly find matching domains within large query sequences.
- **Dynamic Visualization:** Leverages `matplotlib` to dynamically draw a horizontal sequence map.
- **Residue-Level Accuracy:** Displays the query sequence character-by-character along the top axis, allowing researchers to visually confirm exactly which amino acids (e.g., specific domains or motif regions) are resolved in each PDB structure.

## 💻 Technologies Used
- **Python 3.x**
- **Biopython** (`PDBList`, `MMCIF2Dict`, `Align`)
- **Requests** (REST API Integration)
- **Matplotlib** (Data Visualization)
- Optimized for **Google Colab / Jupyter Notebook** environments.

## 📊 Output Example
- **`protein_data.tsv`**: When opened in spreadsheet software, this file functions as a powerful database that allows instant filtering of structures bound to specific ligands or in specific complex states.
- **`sequence_coverage_map_with_seq.png`**: A publication-quality schematic that clearly illustrates the structural coverage of available PDB entries against your target protein sequence.
