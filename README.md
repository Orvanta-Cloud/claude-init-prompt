# 📋 Copy & Paste this prompt into Claude Code:

Here is a universal "init" prompt. You can save this in your notes and paste it into Claude Code whenever you clone a new repository or start a fresh project.

Instead of hardcoding a specific language, this prompt instructs Claude to investigate the project first, figure out the tech stack on its own, and generate the 7-part architecture perfectly tailored to whatever it finds.

```text
Please bootstrap a comprehensive, persistent Claude Code workspace configuration for this project. I want to eliminate "cold starts" and give you a permanent memory of how this project works.

STEP 1: INVESTIGATE
Before generating any files, scan the root directory. Look for dependency files (package.json, composer.json, pyproject.toml, go.mod, etc.), build files, and source code to deduce the tech stack, framework, and likely testing/build commands.

STEP 2: GENERATE STRUCTURE
Using your file creation tools, scaffold the following exact directory and file structure based on what you discovered:

1️⃣ CLAUDE.md & CLAUDE.local.md
- Create `CLAUDE.md` at the root. Write a project overview, document the detected tech stack, architecture, and the commands needed to run/build this project locally.
- Create `CLAUDE.local.md` as a template for machine-specific details (local DBs, absolute paths, environment vars). Add a note that it should remain uncommitted.

2️⃣ .mcp.json
- Create `.mcp.json` at the root. Set up standard MCP integrations (e.g., standard GitHub/Git configurations) and placeholders for any databases or services typical for this stack.

3️⃣ .claude/settings.json & .claude/settings.local.json
- Create the `.claude/` directory.
- Create `settings.json` to define necessary tool permissions, enabling required shell execution permissions for standard dev tasks.
- Create an empty/template `settings.local.json` for developer overrides.

4️⃣ .claude/rules/
- Create this directory and generate three context-specific rule files:
  - `code-style.md`: Define standard formatting conventions appropriate for the detected language(s).
  - `testing.md`: Outline testing conventions based on the testing framework you suspect this project uses.
  - `git-conventions.md`: Rules for commit message formats and branch naming.

5️⃣ .claude/commands/ & .claude/skills/
- Create `.claude/commands/` and add 1-2 standard slash commands based on the stack (e.g., `serve.md`, `build.md`, or `test.md`) that execute the appropriate local shell commands.
- Create `.claude/skills/debugging/` and add a `SKILL.md` explaining how you should approach debugging in this specific language/framework, including what logs to check.

6️⃣ .claude/agents/
- Create this directory and add `code-reviewer.md`.
- Give this sub-agent a strict persona: A Senior Developer expert in this specific tech stack. Instruct it on standard security practices and common pitfalls for this language to check before code is committed.

7️⃣ .claude/hooks/
- Create this directory and write a `pre-commit-validate.sh` bash script.
- Write a basic script that runs the standard linter or syntax checker for the detected primary language. Make sure the script includes `chmod +x` instructions or attempts to make itself executable.

STEP 3: REPORT
Execute the creation of these folders and files now. Once finished, give me a brief summary of the tech stack you detected, what you created, and if there are any specific local settings I should fill in right now.
```

## 💡 Pro-Tip for using this:
Since you want to use this frequently, you can save this text in a tool like TextExpander, Raycast (if you use a Mac), or as an alias in your terminal. This way, whenever you open Claude Code in a new directory, you can just type a quick snippet (like `!claudeinit`) to paste this entire block and watch it instantly configure the workspace.
