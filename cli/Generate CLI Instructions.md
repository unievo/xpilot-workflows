# Workflow for Creating CLI Tool Instructions

Arguments for this workflow: the name of the CLI tool (e.g., `tool_name`).
If no arguments are provided, ask for the tool name.

This workflow is for creating instruction files based on information from a CLI tool help menu. 
You will use the tool cli commands in terminal to create or update the instructions for the tool.

Use this command for the top level commands:

```bash
{tool_name} -h
```

Use this command for any available sub-commands:

```bash
{tool_name} [command] -h
```

For each command and sub-commands you will go recursively using -h to detail all other sub-commands and their parameters.

## Brief overview
- Guidelines for documenting CLI commands and sub-commands for the specified tool, based on the current project workflow.
- These rules are specific to the structure, style, and conventions used in the generated instruction files for specified tool.

## Exclusions
- Do not generate instructions for disabled or obsolete commands and parameters.

## Directory structure
- Create the main directory named `{tool_name}` in the workspace directory.
- Create the main table of contents file for the tool named `{tool_name}.md` and place it in the main directory.
- Each top-level tool command must have its own sub-folder inside a `./content/` sub-directory under the main directory `./content/{command}/`.
- For commands and subcommands, instruction file naming should follow the pattern: `{tool_name}-{command}[-{subcommand}].md` within its respective command sub-folder.
- Instruction files for commands and subcommands must be placed in the corresponding sub-folder `./content/{command}/{file}.md`.

## Linking and references
- In the main table of contents `{tool_name}.md` file, for each top-level command, create a command section named `## [Command name] (Short description of command (from available -h output))`.
- Under the command section, add links to all the sub-commands using the following format:
  - `[Short description of sub-command (from available -h output)](./content/{command}/{file}.md)`

## Formatting and style
- Use clear markdown headings and bullet points for parameters and examples.
- Do not use emojis or special characters in parameter descriptions or examples.
- All descriptions must be concise.

## Content file formatting
- Each instruction file must use the following section order:
  1. Title as a level 1 heading (`#`)
  2. Succinct summary or purpose
  3. "Usage" section with a code block showing the CLI usage
  4. "Parameters" section as a bulleted list, each with name, type, and description
  5. "Example" or "Examples" section with one or more code blocks
- Use only standard Markdown syntax (no HTML).
- Do not include extra whitespace or decorative lines.
- Example markdown structure:

{
  # {tool_name} [command] [subcommand]

  Tool description.

  ## Usage

  ```bash
  {tool_name} [command] [subcommand] [options]
  ```

  ## Parameters

  - `--param1 PARAM`  
    Description.

  - `--param2 PARAM`  
    Description.

  ## Example

  ```bash
  {tool_name} [command] [subcommand] --param value
  ```
}

## Parameter documentation
- List each parameter with its name, type, and a brief description.
- Do not include icons, emojis, or non-standard symbols.
- Include examples given for parameters.
- Provide usage examples for each command, using only standard ASCII characters.

## Update and maintenance
- Append new content in main file, do not overwrite or delete any existing content
- When CLI help output changes, update the corresponding instruction file to match the latest parameters and options.
- Ensure consistency in formatting and terminology across all instruction files.

## Communication style
- Use direct, technical language.
- Avoid verbosity and conversational filler.
- Focus on clarity and precision in all documentation.



