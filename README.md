# dailyjobscanner

A modular, multi-source daily job scanner powered by Google Apps Script. Automatically scans job alert emails and job sites, analyzes role fit using AI, and writes results to Google Sheets.

## AI Stack
- **Primary model:** DeepSeek V4 Flash via [OpenRouter](https://openrouter.ai)
- **Fallback model:** OpenAI GPT-4o
- API keys stored securely in Google Apps Script Properties (never hardcoded)

## Scanners

| Folder | Source | Status |
|--------|--------|--------|
| `jobright/` | Jobright Gmail alerts | Active |
| `linkedin/` | LinkedIn job alerts | Coming soon |
| `indeed/` | Indeed job alerts | Coming soon |

## Structure

```
dailyjobscanner/
  jobright/
    Code.gs       # Google Apps Script for Jobright Gmail scanner
  linkedin/       # Placeholder for LinkedIn scanner (coming soon)
  README.md
```

## How It Works

1. Gmail alert emails from job sites are scanned automatically on a daily trigger
2. Each job listing is extracted and sent to the LLM for fit analysis against your profile
3. Results (verdict, score, tailored bullets, gaps) are written to a Google Sheet
4. Optionally view results via a deployed Web App dashboard

## Setup (Jobright Scanner)

1. Copy `jobright/Code.gs` into a new Google Apps Script project
2. Run `setOpenRouterKey()` once to store your OpenRouter API key
3. Run `setOpenAiKey()` once to store your OpenAI API key (fallback)
4. Run `createScanSheet()` once to create the output Google Sheet
5. Add a daily time-driven trigger on `runScan()`
