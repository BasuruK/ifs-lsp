# ifs-lsp

IFS Marble/PLSQL Language Server for Claude Code, providing code intelligence, static validation, code generation, and database deployment for IFS applications.

## Supported Extensions

`.plsql`, `.plsvc`, `.fragment`, `.ins`, `.client`, `.projection`, `.entity`, `.cre`, `.cdb`, `.upg`

## Prerequisites

- **Java** must be installed and in your system `PATH`
  ```bat
  java -version
  ```
- The IFS build tasks JAR at `C:/IFS/Codegen/ifs-dev-buildtasks.jar`

## Installation

### Step 1: Enable LSP Tool

Add to your global settings (`~/.claude/settings.json`):

```json
{
  "env": {
    "ENABLE_LSP_TOOL": "1"
  }
}
```

### Step 2: Install the Plugin

```bat
claude plugin marketplace add file:///C:/Users/BASBLK/.claude/plugins/cache/ifs-lsp
```

Or use the full path:

```bat
claude plugin install ifs-lsp@file:///C:/Users/BASBLK/.claude/plugins/cache/ifs-lsp/ifs-lsp/1.0.0
```

### Step 3: Restart Claude Code

LSP servers initialize at startup. After installing, fully restart Claude Code.

## Verification

After restart, open a `.plsql` or `.mbl` file and run:

```
/lsp goToDefinition MyFunction
```

Or check debug logs:

```bat
claude --debug
```

Look for:
```
LSP server plugin:ifs-lsp:ifs initialized
LSP server instance started: plugin:ifs-lsp:ifs
```

## Capabilities

- **Go to Definition** — Jump to symbol definitions
- **Find References** — Locate all usages of a symbol
- **Hover** — View type/info on hover
- **Diagnostics** — Real-time static validation
- **Code Completion** — IFS-aware completions
- **Code Generation** — Generate Marble and PLSQL code
- **Database Deployment** — Deploy changes to IFS databases

## Troubleshooting

**"No LSP server available"**
- Ensure `ENABLE_LSP_TOOL=1` is set in settings.json
- Verify Java is in PATH: `java -version`
- Verify the JAR path in `.lsp.json` matches the actual location
- Restart Claude Code completely after changes

**Server not starting**
- Test the JAR manually: `java -jar C:/IFS/Codegen/ifs-dev-buildtasks.jar -lsp`
- Check for Java runtime errors in the output
