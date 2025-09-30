# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-page LLM cost calculator application built with vanilla HTML, CSS, and JavaScript. The application calculates and compares costs across different LLM providers (Anthropic, OpenAI, Google) based on input/output token usage.

## Architecture

- **Single File Application**: All code (HTML, CSS, JavaScript) is contained in `index.html`
- **No Build Process**: This is a static HTML file that runs directly in the browser
- **No Dependencies**: Pure vanilla JavaScript with no external libraries or frameworks

## Key Components

### Data Model
- Model pricing data is hardcoded in the `models` array (line 143-175 in index.html)
- Prices are stored per million tokens for both input and output

### Calculation Logic
- `calculateAndRender()` function (line 183-222) handles:
  - Reading token inputs
  - Computing costs per message (1x, 3x, 10x)
  - Sorting models by cost (most expensive first)
  - Rendering results to the table
  - Classifying models as "Gama Alta" (>$0.001) or "Económico"

## Running the Application

Open `index.html` directly in a web browser. No build step or server required.

## Deployment

### GitHub Pages

The site is configured to deploy via GitHub Pages from the `main` branch root directory.

**Initial Setup:**
1. Go to repository Settings → Pages
2. Set Source to "Deploy from a branch"
3. Select branch: `main` and folder: `/ (root)`
4. Save

**Deploying Updates:**
Simply push changes to the `main` branch. GitHub Pages will automatically redeploy.

## Making Changes

When updating model pricing:
- Edit the `models` array in the `<script>` section
- Maintain the structure: `name`, `inputPrice`, `outputPrice` (prices per million tokens)

When modifying the calculation logic or thresholds:
- The classification threshold is at line 208: `model.cost1 > 0.001`
- All costs are calculated in the `calculateAndRender()` function
