# Annual-report RAG - 15 technology parameters (8 GB RAM, CPU-only laptop)

Tuned for: Intel i5-1240P, 8 GB RAM, Intel Iris Xe (no NVIDIA). LLM = gpt-oss-120b on Groq (cloud).

## Folder
```
annual_report_rag_8GB/
  annual_report_rag_8GB.ipynb   <- open this in VS Code
  Company_data.csv              <- your company list
  annual_reports/               <- put ALL PDFs here
  requirements.txt
  groq_key.txt                  <- (optional) your key, one line
  tech_matrix_output/           <- created automatically
      tech_matrix_all.xlsx      <- THE one Excel (Tech Matrix + Evidence sheets)
      match_report.csv          <- company -> PDF matching result
      cell_cache.json           <- backup of every answer
      indexes/                  <- saved chunks/embeddings per PDF
```

## One-time setup (PowerShell, inside this folder)
```
python -m venv .venv
.venv\Scripts\activate
pip install torch --index-url https://download.pytorch.org/whl/cpu
pip install -r requirements.txt
```
VS Code: install extensions "Python" and "Jupyter", open the folder, open the notebook, choose the `.venv` kernel.

## Groq key
1. console.groq.com -> API Keys -> Create (gsk_...).
2. EITHER save it in a file `groq_key.txt` (one line) next to the notebook, OR paste it when the Section 9b cell asks.

## Every run
1. Edit Section 9: START_COMPANY / END_COMPANY (1-based position in Company_data.csv).
2. Run Section 9, 9b, 10, 11, 11b, 11c, then Section 12 (or Run All).
3. Close the Excel file before running. New ranges are appended to the same Excel; companies already in it are skipped.

## Tips for 8 GB RAM
- Close Chrome/Teams/Excel while running. Run 1-3 companies at a time at first.
- If the laptop freezes: restart the kernel and run one company (START = END). Everything finished is cached.
- Groq free tier has per-minute and per-day token limits. If you see "STOP: rate/daily limit", wait and re-run Section 12 - nothing is lost.
