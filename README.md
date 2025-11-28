# Nano PDF Editor

A CLI tool to edit PDF slides using natural language prompts, powered by Google's **Gemini 3 Pro Image** ("Nano Banana") model.

## Features
*   **Natural Language Editing**: "Make the header blue", "Fix the typo", "Change the chart to a bar graph".
*   **Context-Aware**: Understands the visual style of your deck (fonts, colors, layout) by analyzing reference slides.
*   **Non-Destructive**: Preserves the searchable text layer of your PDF using OCR re-hydration.
*   **Multi-page & Parallel**: Edit multiple pages in a single command with concurrent processing.

## Installation

```bash
pip install nano-pdf
```

## Configuration

You need a Google Gemini API key. Set it as an environment variable:

```bash
export GEMINI_API_KEY="your_api_key_here"
```

## Usage

### Basic Edit
Edit a single page (e.g., Page 2):

```bash
nano-pdf edit my_deck.pdf 2 "Change the title to 'Q3 Results'"
```

### Multi-page Edit
Edit multiple pages in one go:

```bash
nano-pdf edit my_deck.pdf 1 "Update date to Oct 2025" 5 "Add company logo" 10 "Fix typo in footer"
```

### Options
*   `--use-context`: Include the full text of the PDF as context for the model. (Disabled by default to prevent hallucinations).
*   `--style-refs "1,5"`: Manually specify which pages to use as style references.
*   `--output "new.pdf"`: Specify the output filename.

## Requirements
*   Python 3.10+
*   `poppler` (for PDF rendering)
*   `tesseract` (for OCR)

### System Dependencies (macOS)
```bash
brew install poppler tesseract
```

## License
MIT
