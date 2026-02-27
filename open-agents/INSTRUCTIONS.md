# Open Agent System Instructions

An open agent system for general-purpose file management, research, and content transformation.

---

## How This System Works

1. **Entry points** (CLAUDE.md/AGENTS.md/GEMINI.md) point here
2. **This file** is the index—it describes available agents
3. **Agent files** load on demand when triggered

---

## Available Agents

### 1. The Researcher (`agents/researcher.md`)

**Purpose:** Research topics and produce comprehensive markdown articles with citations and structured information.

**When to use:**
- User asks to "research" a topic
- User asks to "investigate" or "look into" something
- User asks to "expand" an existing article
- User provides a stub file and wants it filled in

**Output:** Markdown files in `open-agents/output-drafts/`

### 2. The Transformer (`agents/transformer.md`)

**Purpose:** Transform content between different formats (Markdown ↔ HTML, JSON ↔ CSV, etc.)

**When to use:**
- User asks to "convert" between formats
- User asks to "transform" or "reformat" content
- User asks to "create HTML" or "generate JSON" from existing files

**Output:** Transformed files in `open-agents/output-refined/`

### 3. The Publisher (`agents/publisher.md`)

**Purpose:** Finalize content for publication, ensuring quality and consistency.

**When to use:**
- User asks to "finalize" or "publish" content
- User asks to "prepare for release"
- User requests final QA and polish

**Output:** Publication-ready files in `open-agents/output-final/`

### 4. The Financial Analyst (`agents/financial_analyst.md`)

**Purpose:** Analyze stocks and financial markets to identify promising long-term investment opportunities based on fundamental analysis, technical analysis and risk assessment.

**When to use:**
- User asks to "analyze" or "evaluate" a stock
- User asks for "stock recommendations" or "investment ideas"
- User wants company financial health analysis
- User asks about "best stocks for long-term investment"
- User requests sector or industry comparisons
- User asks for portfolio building help

**Output:** Stock analysis reports in `open-agents/output-drafts/`

### 5. The ASCII Artist (`agents/ascii_artist.md`)

**Purpose:** Convert text and content into creative ASCII art representations using characters, symbols, and formatting.

**When to use:**
- User asks to "convert text to ASCII art"
- User asks to "create ASCII banner" or "ASCII logo"
- User requests decorative text for README files
- User wants terminal art or text art
- User asks for section dividers in code
- User wants to create visual text representations

**Output:** ASCII art files in `open-agents/output-refined/`

---

## Routing Logic

| User says... | Agent |
|--------------|-------|
| "Research [topic]" | Researcher |
| "Investigate [topic]" | Researcher |
| "Expand this article" | Researcher |
| "Convert to HTML" | Transformer |
| "Transform to JSON" | Transformer |
| "Reformat as [format]" | Transformer |
| "Finalize [file]" | Publisher |
| "Prepare for publication" | Publisher |
| "Create and finalize [topic]" | Researcher → Transformer → Publisher |
| "Analyze [stock ticker]" | Financial Analyst |
| "Evaluate [company] stock" | Financial Analyst |
| "Best stocks for long-term" | Financial Analyst |
| "Stock recommendations" | Financial Analyst |
| "Compare [stocks/sector]" | Financial Analyst |
| "Build investment portfolio" | Financial Analyst |
| "Convert text to ASCII art" | ASCII Artist |
| "Create ASCII banner" | ASCII Artist |
| "Make ASCII logo" | ASCII Artist |
| "ASCII art for [text]" | ASCII Artist |
| "Create code divider" | ASCII Artist |

---

## Workflow Patterns

### Simple Research
1. User: "Research [topic]"
2. Researcher creates draft in `output-drafts/`
3. Done

### Full Pipeline
1. User: "Create and finalize article on [topic]"
2. Researcher creates draft in `output-drafts/`
3. Transformer refines in `output-refined/`
4. Publisher finalizes in `output-final/`

### Transform Existing Content
1. User: "Convert [file] to HTML"
2. Transformer reads source and creates HTML in `output-refined/`
3. Done

### Stock Analysis
1. User: "Analyze Microsoft stock for long-term investment"
2. Financial Analyst researches company fundamentals, valuations, and risks
3. Creates comprehensive analysis in `output-drafts/`
4. Done

### Portfolio Building
1. User: "Build a diversified portfolio for retirement"
2. Financial Analyst analyzes multiple stocks across sectors
3. Creates portfolio recommendations in `output-drafts/`
4. Done

### ASCII Art Creation
1. User: "Create ASCII art banner for 'My Project'"
2. ASCII Artist generates multiple style variations
3. Creates ASCII art file in `output-refined/`
4. Done

---

## File Naming Conventions

- **Drafts:** `topic_name.md` (lowercase, underscores)
- **Refined:** `topic_name_refined.html` (adds format extension)
- **Final:** `topic_name_final.html` (adds final suffix)
- **Stock Analysis:** `[ticker]_analysis.md` (e.g., `msft_analysis.md`)
- **Portfolio Reports:** `portfolio_recommendations_[date].md`
- **ASCII Art:** `ascii_[text]_[date].txt` or `.md` (e.g., `ascii_hello_world_2026-01-13.txt`)

---

## Adding New Agents

To add a new agent:

1. Create `open-agents/agents/your_agent.md` with full definition
2. Add entry to "Available Agents" section above
3. Add routing rules to "Routing Logic" table
4. Create corresponding slash commands in `.claude/commands/` and `.gemini/commands/`
5. Test by invoking with natural language or slash commands

See the [OpenAgentDefinition.md](../open-agent-system/OpenAgentDefinition.md) for complete agent creation guidelines.

---

## Tips for Using This System

- **Be specific:** "Research the history of video games" is better than "research games"
- **Use the source folder:** Add stub files or notes to `source/` to give agents context
- **Check output folders:** Agents save work in `output-drafts/`, `output-refined/`, or `output-final/`
- **Chain operations:** Ask for multi-step workflows like "research, transform, and publish"
- **Review outputs:** Always review agent output before considering it final

---

*This system is tool-agnostic and works with Claude Code, Gemini CLI, and Codex.*
