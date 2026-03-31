# FinancialResearcher-Agent-using-CrewAI

# FinancialResearcher Crew

An AI-powered company research pipeline built with crewAI.

This project runs a two-agent workflow:
- A research agent gathers company information from the web.
- An analyst agent turns the research into a polished report.

By default, the project is configured to research Apple and generate a report at `output/report.md`.

## What This Project Does

The crew executes two sequential tasks:

1. **Research task**
	 - Covers company status/health, historical performance, challenges and opportunities, recent events, and future outlook.
2. **Analysis task**
	 - Produces a structured report with executive summary, analysis, and market outlook disclaimer.

## Project Structure

- `src/financial_researcher/main.py` - Entry point that runs the crew.
- `src/financial_researcher/crew.py` - Agent and task wiring.
- `src/financial_researcher/config/agents.yaml` - Agent roles, goals, and models.
- `src/financial_researcher/config/tasks.yaml` - Task prompts and expected outputs.
- `output/report.md` - Final generated report file.

## Requirements

- Python `>=3.10,<3.13`
- `uv` package manager
- API keys:
	- `OPENAI_API_KEY` (for model access)
	- `SERPER_API_KEY` (for web search tool)

## Setup

1. Install `uv` (if you do not already have it):

```bash
pip install uv
```

2. Install project dependencies from this folder:

```bash
uv sync
```

3. Create a `.env` file in this folder:

```env
OPENAI_API_KEY=your_openai_key
SERPER_API_KEY=your_serper_key
```

## Run

From this project folder, run:

```bash
crewai run
```

What happens:
- The crew starts with the configured input company (`Apple` in `main.py`).
- The researcher gathers information.
- The analyst writes the final report.
- The report is saved to `output/report.md`.

## Change the Company

Edit the input in `src/financial_researcher/main.py`:

```python
inputs = {
		'company': 'Apple'
}
```

Replace `'Apple'` with another company name and run again.

## Customize Agents and Tasks

- Update agent behavior and model selection in `src/financial_researcher/config/agents.yaml`.
- Improve prompt quality and output requirements in `src/financial_researcher/config/tasks.yaml`.
- Add extra tools or logic in `src/financial_researcher/crew.py`.

## Common Issues

- **No or poor research quality**
	- Strengthen task prompts in `tasks.yaml` to require citations, dates, and multiple sources.
- **Tool not returning web results**
	- Verify `SERPER_API_KEY` is set correctly.
- **Model authentication errors**
	- Verify `OPENAI_API_KEY` is valid and available in environment variables.
- **Dependency/runtime errors**
	- Re-run `uv sync` and confirm Python version compatibility.

## Notes

- This project is for research and educational use.
- Generated reports are not investment advice.
