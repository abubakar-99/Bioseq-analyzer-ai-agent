
# BioSeq Analyzer AI

An **intelligent AI agent** for bioinformatics sequence analysis using **LangGraph**. This tool performs DNA, RNA, and protein analysis through natural language conversations with dynamic tool orchestration.

---

## Features

* **Natural Language Interface:** Interact using plain English queries.
* **Intelligent Tool Selection:** LLM-based reasoning for automatic tool orchestration.
* **5 Specialized Tools:**

  1. **Sequence Alignment:** Needleman-Wunsch global alignment.
  2. **ORF Detection:** 6-frame translation for identifying protein-coding regions.
  3. **Motif Finder:** Pattern matching for conserved sequences.
  4. **Structure Prediction:** Secondary structure prediction.
  5. **Statistics Calculator:** Composition analysis of sequences.
* **Stateful Conversations:** Maintains context across interactions.
* **Comprehensive Results:** Detailed analysis with biological interpretation.

---

## Quick Start

### Prerequisites

* Python 3.8 or higher
* OpenAI API key

### Installation

Clone the repository:

```bash
git clone https://github.com/abubakar-99/bioseq-analyzer.git
cd bioseq-analyzer
```

Create and activate a virtual environment:

```bash
python -m venv venv
# On Linux/macOS
source venv/bin/activate
# On Windows
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Set up environment variables:

```bash
export OPENAI_API_KEY='your-api-key-here'  # Linux/macOS
setx OPENAI_API_KEY "your-api-key-here"     # Windows
```

---

## Usage

### Basic Usage

```python
from bioseq_agent import app
from langchain_core.messages import HumanMessage

# Run a query
result = app.invoke({
    "messages": [HumanMessage(content="Align ATCGATCG and ATCGATGG")]
})

# Print result
for msg in result["messages"]:
    print(msg.content)
```

### Demo Script

Run demonstration queries showcasing all tools:

```bash
python bioseq_agent.py
```

---

## Example Queries

```python
# Sequence Alignment
"Align these DNA sequences: ATCGATCGATCG and ATCGATGGATCG"

# ORF Detection
"Find all ORFs in sequence: ATGTACTAGCTAGATGTAACCCATGAAATAG"

# Motif Finding
"Find the TATA motif in: GCATATATATACGCGCTATATAGG"

# Statistics
"Calculate GC content of: ATCGATCGATCGGGCCTA"

# Structure Prediction
"Predict secondary structure of protein: MKTAYIAKQRQISITPDVQMK"
```

---

## Tools Documentation

### 1. Sequence Alignment

* **Purpose:** Pairwise alignment of DNA/RNA/protein sequences
* **Algorithm:** Needleman-Wunsch global alignment
* **Input:** Two sequences (`seq1`, `seq2`)
* **Output:** Alignment score, identity percentage, visual alignment

```python
sequence_alignment("ATCGATCG", "ATCGATGG")
```

---

### 2. ORF Detection

* **Purpose:** Identify potential protein-coding regions
* **Algorithm:** 6-frame translation with start/stop codon detection
* **Input:** DNA sequence, minimum length (optional)
* **Output:** Reading frame, position (start-end), DNA sequence, translated protein

```python
orf_detection("ATGTACTAGCTAGATGTAA", min_length=30)
```

---

### 3. Motif Finder

* **Purpose:** Find conserved sequence patterns
* **Algorithm:** Boyer-Moore string searching
* **Input:** Sequence and motif pattern
* **Output:** Occurrence count, positions found, context display

```python
motif_finder("ATATATATACGATA", "TATA")
```

---

### 4. Structure Prediction

* **Purpose:** Predict protein secondary structure
* **Algorithm:** Simplified Chou-Fasman method
* **Input:** Protein sequence
* **Output:** Structure assignment (H/E/C), composition percentages, structure visualization

```python
structure_prediction("MKTAYIAKQRQ")
```

---

### 5. Statistics Calculator

* **Purpose:** Sequence composition analysis
* **Algorithm:** Nucleotide counting and analysis
* **Input:** DNA/RNA sequence
* **Output:** Nucleotide composition, GC content, molecular weight, quality metrics

```python
statistics_calculator("ATCGATCGATCGGGCCTA")
```

---

## License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.


