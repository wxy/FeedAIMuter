

<skills_system priority="1">

## Available Skills

<!-- SKILLS_TABLE_START -->
<usage>
When users ask you to perform tasks, check if any of the available skills below can help complete the task more effectively. Skills provide specialized capabilities and domain knowledge.

How to use skills:
- Invoke: Bash("openskills read <skill-name>")
- The skill content will load with detailed instructions on how to complete the task
- Base directory provided in output for resolving bundled resources (references/, scripts/, assets/)

Usage notes:
- Only use skills listed in <available_skills> below
- Do not invoke a skill that is already loaded in your context
- Each skill invocation is stateless
</usage>

<available_skills>

<skill>
<name>algorithmic-art</name>
<description>Creating algorithmic art using p5.js with seeded randomness and interactive parameter exploration. Use this when users request creating art using code, generative art, algorithmic art, flow fields, or particle systems. Create original algorithmic art rather than copying existing artists' work to avoid copyright violations.</description>
<location>project</location>
</skill>

<skill>
<name>brand-guidelines</name>
<description>Applies Anthropic's official brand colors and typography to any sort of artifact that may benefit from having Anthropic's look-and-feel. Use it when brand colors or style guidelines, visual formatting, or company design standards apply.</description>
<location>project</location>
</skill>

<skill>
<name>canvas-design</name>
<description>Create beautiful visual art in .png and .pdf documents using design philosophy. You should use this skill when the user asks to create a poster, piece of art, design, or other static piece. Create original visual designs, never copying existing artists' work to avoid copyright violations.</description>
<location>project</location>
</skill>

<skill>
<name>doc-coauthoring</name>
<description>Guide users through a structured workflow for co-authoring documentation. Use when user wants to write documentation, proposals, technical specs, decision docs, or similar structured content. This workflow helps users efficiently transfer context, refine content through iteration, and verify the doc works for readers. Trigger when user mentions writing docs, creating proposals, drafting specs, or similar documentation tasks.</description>
<location>project</location>
</skill>

<skill>
<name>docx</name>
<description>"Comprehensive document creation, editing, and analysis with support for tracked changes, comments, formatting preservation, and text extraction. When Claude needs to work with professional documents (.docx files) for: (1) Creating new documents, (2) Modifying or editing content, (3) Working with tracked changes, (4) Adding comments, or any other document tasks"</description>
<location>project</location>
</skill>

<skill>
<name>frontend-design</name>
<description>Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build web components, pages, artifacts, posters, or applications (examples include websites, landing pages, dashboards, React components, HTML/CSS layouts, or when styling/beautifying any web UI). Generates creative, polished code and UI design that avoids generic AI aesthetics.</description>
<location>project</location>
</skill>

<skill>
<name>internal-comms</name>
<description>A set of resources to help me write all kinds of internal communications, using the formats that my company likes to use. Claude should use this skill whenever asked to write some sort of internal communications (status reports, leadership updates, 3P updates, company newsletters, FAQs, incident reports, project updates, etc.).</description>
<location>project</location>
</skill>

<skill>
<name>mcp-builder</name>
<description>Guide for creating high-quality MCP (Model Context Protocol) servers that enable LLMs to interact with external services through well-designed tools. Use when building MCP servers to integrate external APIs or services, whether in Python (FastMCP) or Node/TypeScript (MCP SDK).</description>
<location>project</location>
</skill>

<skill>
<name>pdf</name>
<description>Comprehensive PDF manipulation toolkit for extracting text and tables, creating new PDFs, merging/splitting documents, and handling forms. When Claude needs to fill in a PDF form or programmatically process, generate, or analyze PDF documents at scale.</description>
<location>project</location>
</skill>

<skill>
<name>pptx</name>
<description>"Presentation creation, editing, and analysis. When Claude needs to work with presentations (.pptx files) for: (1) Creating new presentations, (2) Modifying or editing content, (3) Working with layouts, (4) Adding comments or speaker notes, or any other presentation tasks"</description>
<location>project</location>
</skill>

<skill>
<name>skill-creator</name>
<description>Guide for creating effective skills. This skill should be used when users want to create a new skill (or update an existing skill) that extends Claude's capabilities with specialized knowledge, workflows, or tool integrations.</description>
<location>project</location>
</skill>

<skill>
<name>slack-gif-creator</name>
<description>Knowledge and utilities for creating animated GIFs optimized for Slack. Provides constraints, validation tools, and animation concepts. Use when users request animated GIFs for Slack like "make me a GIF of X doing Y for Slack."</description>
<location>project</location>
</skill>

<skill>
<name>template</name>
<description>Replace with description of the skill and when Claude should use it.</description>
<location>project</location>
</skill>

<skill>
<name>theme-factory</name>
<description>Toolkit for styling artifacts with a theme. These artifacts can be slides, docs, reportings, HTML landing pages, etc. There are 10 pre-set themes with colors/fonts that you can apply to any artifact that has been creating, or can generate a new theme on-the-fly.</description>
<location>project</location>
</skill>

<skill>
<name>web-artifacts-builder</name>
<description>Suite of tools for creating elaborate, multi-component claude.ai HTML artifacts using modern frontend web technologies (React, Tailwind CSS, shadcn/ui). Use for complex artifacts requiring state management, routing, or shadcn/ui components - not for simple single-file HTML/JSX artifacts.</description>
<location>project</location>
</skill>

<skill>
<name>webapp-testing</name>
<description>Toolkit for interacting with and testing local web applications using Playwright. Supports verifying frontend functionality, debugging UI behavior, capturing browser screenshots, and viewing browser logs.</description>
<location>project</location>
</skill>

<skill>
<name>xlsx</name>
<description>"Comprehensive spreadsheet creation, editing, and analysis with support for formulas, formatting, data analysis, and visualization. When Claude needs to work with spreadsheets (.xlsx, .xlsm, .csv, .tsv, etc) for: (1) Creating new spreadsheets with formulas and formatting, (2) Reading or analyzing data, (3) Modify existing spreadsheets while preserving formulas, (4) Data analysis and visualization in spreadsheets, or (5) Recalculating formulas"</description>
<location>project</location>
</skill>

</available_skills>
<!-- SKILLS_TABLE_END -->

<!-- EVOSKILLS_START -->
<skills_system priority="1">

## Available Skills (evoskills)

<!--
SKILLS_TABLE_START -->
<usage>
When users ask you to perform tasks, check if any of the
available skills below can help complete the task more effectively. Skills provide
specialized capabilities and domain knowledge.

How to use skills:
- Invoke: Bash("npx openskills read <skill-name>")
- The skill content will load with detailed instructions on how to complete the task
- Base directory provided in output for resolving bundled resources (references/, scripts/, assets/)

Usage notes:
- Only use skills listed in <available_skills> below
- Do not invoke a skill that is already loaded in your context
- Each skill invocation is stateless
</usage>

<available_skills>

<!-- Tier 1: Core Skills (2) - Evolution Infrastructure -->

<skill>
<name>_evolution-core</name>
<description>Identify improvement opportunities and patterns in code and processes. Proposes enhancements based on architectural patterns and best practices. Core mechanism of continuous system evolution.</description>
<location>project</location>
</skill>

<skill>
<name>_skills-manager</name>
<description>Core skill manager for evoskills. Handles skill lifecycle (init, install, remove, update) and skill contributions. Core mechanism managing the skill ecosystem.</description>
<location>project</location>
</skill>


<!-- Tier 2: System Skills (4) - Required for Safe Operation -->

<skill>
<name>_instruction-guard</name>
<description>Read and apply directives before processing each request. Enforces instruction hierarchy and prevents instruction conflicts.</description>
<location>project</location>
</skill>

<skill>
<name>_context-ack</name>
<description>Format responses with clear headers, footers, and reference lists. Ensures proper context acknowledgment and response structure.</description>
<location>project</location>
</skill>

<skill>
<name>_file-output-guard</name>
<description>Validate and safeguard all file creation operations. Prevents unsafe file creation patterns and unauthorized modifications.</description>
<location>project</location>
</skill>

<skill>
<name>_execution-precheck</name>
<description>Validate dependencies and runtime requirements before executing commands. Ensures all prerequisites are met before task execution.</description>
<location>project</location>
</skill>


<!-- Tier 3: Optional Skills (8) - User-Selectable Enhancements -->

<skill>
<name>_git-commit</name>
<description>Implement conventional commits workflow. Ensures proper commit message formatting and semantic versioning compliance.</description>
<location>project</location>
</skill>

<skill>
<name>_pr-creator</name>
<description>Automate PR generation with version detection and release notes. Streamlines contributions and version management.</description>
<location>project</location>
</skill>

<skill>
<name>_release-process</name>
<description>Execute complete release workflow. Coordinates versioning, tagging, and publication of releases.</description>
<location>project</location>
</skill>

<skill>
<name>_code-health-check</name>
<description>Perform quality checks before commit. Validates code standards, security, and architectural consistency.</description>
<location>project</location>
</skill>

<skill>
<name>_typescript-type-safety</name>
<description>Enforce TypeScript type safety guidelines. Ensures proper typing and prevents type-related runtime errors.</description>
<location>project</location>
</skill>

<skill>
<name>_change-summary</name>
<description>Summarize completed work sessions. Provides concise summaries of changes and progress made.</description>
<location>project</location>
</skill>

<skill>
<name>_traceability-check</name>
<description>Ensure all decisions are properly documented. Validates decision traceability and documentation completeness.</description>
<location>project</location>
</skill>

<skill>
<name>_session-safety</name>
<description>Prevent state violations and session inconsistencies. Maintains context integrity and prevents conflicting actions.</description>
<location>project</location>
</skill>


</available_skills>
<!--
SKILLS_TABLE_END -->

</skills_system>
<!-- EVOSKILLS_END -->
