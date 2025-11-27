An intelligent AI agent for bioinformatics sequence analysis using LangGraph. Performs DNA/RNA/protein analysis through natural language conversations with dynamic tool orchestration.
 Features

 Natural Language Interface: Interact using plain English queries
 Intelligent Tool Selection: LLM-based reasoning for automatic tool orchestration
 5 Specialized Tools:

Sequence Alignment (Needleman-Wunsch)
ORF Detection (6-frame translation)
Motif Finder (Pattern matching)
Structure Prediction (Secondary structure)
Statistics Calculator (Composition analysis)


Stateful Conversations: Context maintained across interactions
Comprehensive Results: Detailed analysis with biological interpretation
Quick Start
Prerequisites

Python 3.8 or higher
OpenAI API key

Installation

Clone the repository:

bashgit clone https://github.com/abubakar-99/bioseq-analyzer.git
cd bioseq-analyzer

Create virtual environment:

bashpython -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

Install dependencies:

bashpip install -r requirements.txt

Set up environment variables:

bashexport OPENAI_API_KEY='your-api-key-here'
Usage
Basic Usage
pythonfrom bioseq_agent import app
from langchain_core.messages import HumanMessage

# Run a query
result = app.invoke({
    "messages": [HumanMessage(content="Align ATCGATCG and ATCGATGG")]
})

# Print result
for msg in result["messages"]:
    print(msg.content)
Demo Script
bashpython bioseq_agent.py
This will run 5 demonstration queries showcasing all tools.
📚 Example Queries
python# Sequence Alignment
"Align these DNA sequences: ATCGATCGATCG and ATCGATGGATCG"

# ORF Detection
"Find all ORFs in sequence: ATGTACTAGCTAGATGTAACCCATGAAATAG"

# Motif Finding
"Find the TATA motif in: GCATATATATACGCGCTATATAGG"

# Statistics
"Calculate GC content of: ATCGATCGATCGGGCCTA"

# Structure Prediction
"Predict secondary structure of protein: MKTAYIAKQRQISITPDVQMK"
🔧 Tools Documentation
1. Sequence Alignment Tool
Purpose: Pairwise alignment of DNA/RNA/protein sequences
Algorithm: Needleman-Wunsch global alignment
Input: Two sequences (seq1, seq2)
Output:

Alignment score
Identity percentage
Visual alignment

Example:
pythonsequence_alignment("ATCGATCG", "ATCGATGG")
2. ORF Detection Tool
Purpose: Identify potential protein-coding regions
Algorithm: 6-frame translation with start/stop codon detection
Input: DNA sequence, minimum length (optional)
Output:

Reading frame
Position (start-end)
DNA sequence
Translated protein

Example:
pythonorf_detection("ATGTACTAGCTAGATGTAA", min_length=30)
3. Motif Finder Tool
Purpose: Find conserved sequence patterns
Algorithm: Boyer-Moore string searching
Input: Sequence and motif pattern
Output:

Occurrence count
Positions found
Context display

Example:
pythonmotif_finder("ATATATATACGATA", "TATA")
4. Structure Prediction Tool
Purpose: Predict protein secondary structure
Algorithm: Simplified Chou-Fasman method
Input: Protein sequence
Output:

Structure assignment (H/E/C)
Composition percentages
Structure visualization

Example:
pythonstructure_prediction("MKTAYIAKQRQ")
5. Statistics Calculator Tool
Purpose: Sequence composition analysis
Algorithm: Nucleotide counting and analysis
Input: DNA/RNA sequence
Output:

Nucleotide composition
GC content
Molecular weight
Quality metrics
