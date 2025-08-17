# Claude Code User Manual

## Table of Contents
1. [What is Claude Code?](#what-is-claude-code)
2. [Installation](#installation)
3. [Getting Started](#getting-started)
4. [Key Features](#key-features)
5. [Interactive Mode](#interactive-mode)
6. [Common Workflows](#common-workflows)
7. [Memory Management](#memory-management)
8. [Slash Commands](#slash-commands)
9. [Configuration](#configuration)
10. [Keyboard Shortcuts](#keyboard-shortcuts)
11. [Best Practices](#best-practices)

## What is Claude Code?

Claude Code is Anthropic's agentic coding tool designed to help developers turn ideas into code faster. It's an intelligent assistant that works directly in your terminal, capable of understanding complex codebases, writing code, debugging issues, and automating development tasks.

### Key Advantages
- **Terminal-native**: Works directly in your existing development workflow
- **Action-oriented**: Can edit files, run commands, and create commits
- **Highly composable**: Integrates with external tools via Model Context Protocol (MCP)
- **Enterprise-ready**: Robust security and privacy features

### Primary Use Cases
- Feature development from natural language descriptions
- Debugging and fixing code issues
- Code navigation and understanding
- Automating repetitive development tasks
- Code reviews and refactoring

## Installation

### Prerequisites
- Node.js 18 or higher

### Installation Options

#### NPM Install (Recommended)
```bash
npm install -g @anthropic-ai/claude-code
```

#### Native Install

**macOS, Linux, WSL:**
```bash
curl -fsSL claude.ai/install.sh | bash
```

**Windows PowerShell:**
```powershell
irm https://claude.ai/install.ps1 | iex
```

## Getting Started

1. **Navigate to your project directory**
   ```bash
   cd /path/to/your/project
   ```

2. **Start Claude Code**
   ```bash
   claude
   ```

3. **Try initial commands**
   - "what does this project do?"
   - "what technologies does this project use?"
   - "add a hello world function"

### First Session Tips
- Claude Code automatically reads your project files
- It always asks permission before modifying files
- Start with broad questions, then narrow down to specifics
- Use natural language to describe what you want to accomplish

## Key Features

### Intelligent Code Understanding
- Automatically analyzes project structure
- Understands dependencies and technologies in use
- Traces code execution paths
- Identifies patterns and conventions

### File Operations
- Read and analyze files
- Edit existing files with precise changes
- Create new files when necessary
- Search across codebases efficiently

### Git Integration
- Conversational Git operations
- Automatic commit message generation
- Pull request creation
- Branch management

### Task Automation
- Run commands and scripts
- Execute tests and builds
- Handle complex multi-step workflows
- Integration with external tools

## Interactive Mode

Claude Code runs in an interactive terminal session where you can have ongoing conversations about your code.

### Session Management
- **Start a session**: `claude`
- **Exit session**: `Ctrl+D` or type "exit"
- **Clear screen**: `Ctrl+L`
- **Cancel operation**: `Ctrl+C`

### Extended Thinking
For complex problems, Claude can engage in extended thinking by prefacing requests with phrases like:
- "Think deeply about..."
- "Carefully consider..."
- "Take your time to analyze..."

### Conversation Resumption
Use the `--resume` flag to continue previous conversations:
```bash
claude --resume
```

## Common Workflows

### 1. Understanding a Codebase
```
> "Analyze this project and explain its architecture"
> "Where is user authentication handled?"
> "Show me the data flow for user registration"
```

### 2. Feature Development
```
> "I need to add a user profile page with edit functionality"
> "Implement OAuth2 authentication for our API"
> "Add real-time notifications using WebSockets"
```

### 3. Bug Fixing
```
> "There's an error in the login flow, can you help debug it?"
> "Users are reporting slow page loads, can you investigate?"
> "Fix the TypeScript errors in the components directory"
```

### 4. Code Refactoring
```
> "Refactor this component to use hooks instead of class components"
> "Extract reusable logic from these similar functions"
> "Modernize this legacy code to use current best practices"
```

### 5. Testing and Documentation
```
> "Generate unit tests for the authentication module"
> "Add JSDoc comments to the API functions"
> "Create integration tests for the user workflow"
```

## Memory Management

Claude Code uses a hierarchical memory system to maintain context and preferences across sessions.

### Memory Hierarchy (in precedence order)
1. **Enterprise Policy**: Organization-wide instructions
2. **Project Memory**: Team-shared project instructions (`.claude/CLAUDE.md`)
3. **User Memory**: Personal preferences (`~/.claude/CLAUDE.md`)
4. **Local Project Memory**: Project-specific personal notes

### Managing Memory

#### Quick Memory Addition
Use `#` at the start of a message to add to memory:
```
# Remember to use TypeScript strict mode for all new files
```

#### Memory Commands
- `/memory`: Edit memory files
- `/init`: Bootstrap a project's CLAUDE.md

#### Memory File Structure
```markdown
# Project Guidelines

## Coding Standards
- Use TypeScript strict mode
- Follow ESLint configuration
- Write unit tests for new features

## Architecture Notes
- Use Redux for state management
- Components in /src/components
- API calls in /src/services

@path/to/additional/context.md
```

### Memory Best Practices
- Be specific in instructions
- Use structured markdown
- Import additional context files with `@path/to/file`
- Periodically review and update memories

## Slash Commands

Slash commands provide quick access to specific functionality during interactive sessions.

### Built-in Commands
- `/add-dir`: Add additional working directories
- `/agents`: Manage custom AI subagents
- `/clear`: Clear conversation history
- `/help`: Get usage help
- `/model`: Select or change the AI model
- `/review`: Request code review
- `/memory`: Edit memory files
- `/init`: Bootstrap project memory

### Custom Commands
Create custom commands in `.claude/commands/` (project) or `~/.claude/commands/` (personal):

**Example: `.claude/commands/deploy.md`**
```markdown
---
description: Deploy the application to staging
tools: [Bash]
---

Deploy the application to staging environment:

!npm run build
!npm run deploy:staging

Check deployment status and verify the application is running correctly.
```

### MCP Commands
Commands from connected MCP servers follow the format:
```
/mcp__<server-name>__<prompt-name>
```

## Configuration

### Configuration Files
- **User settings**: `~/.claude/settings.json`
- **Project settings**: `.claude/settings.json` (shared)
- **Local project settings**: `.claude/settings.local.json` (personal)

### Common Configuration Commands
```bash
# List all settings
claude config list

# View specific setting
claude config get model

# Set a configuration value
claude config set model claude-3-5-sonnet-20241022

# Global configuration
claude config set -g autoUpdates false
```

### Key Settings

#### Permissions
```json
{
  "permissions": {
    "tools": {
      "Bash": "allow",
      "Edit": "allow",
      "WebFetch": "deny"
    },
    "files": {
      "read": ["**/*"],
      "write": ["src/**/*", "tests/**/*"]
    }
  }
}
```

#### Environment Variables
```json
{
  "env": {
    "NODE_ENV": "development",
    "API_URL": "http://localhost:3000"
  }
}
```

#### Hooks
```json
{
  "hooks": {
    "pre_tool": "echo 'About to run tool'",
    "post_tool": "echo 'Tool execution complete'"
  }
}
```

## Keyboard Shortcuts

### General Shortcuts
- `Ctrl+C`: Cancel current input or generation
- `Ctrl+D`: Exit Claude Code session
- `Ctrl+L`: Clear terminal screen
- `Up/Down arrows`: Navigate command history
- `Esc` + `Esc`: Edit previous message

### Multiline Input
- `\` + `Enter`: Quick escape (works in all terminals)
- `Option+Enter`: Default on macOS
- `Shift+Enter`: After terminal setup
- `Ctrl+J`: Line feed character

### Vim Mode (when enabled)

#### Navigation (NORMAL mode)
- `h/j/k/l`: Move left/down/up/right
- `w`: Next word
- `e`: End of word
- `b`: Previous word
- `0`: Beginning of line
- `$`: End of line

#### Editing
- `x`: Delete character
- `dd`: Delete line
- `D`: Delete to end of line
- `cc`: Change line
- `.`: Repeat last change

## Best Practices

### Effective Communication
1. **Be specific**: Instead of "fix this", explain what's broken and expected behavior
2. **Provide context**: Mention relevant files, functions, or error messages
3. **Break down complex tasks**: Split large features into smaller, manageable pieces
4. **Use domain-specific language**: Technical terms help Claude understand your intent

### Project Organization
1. **Set up CLAUDE.md**: Document project conventions and guidelines
2. **Use memory effectively**: Store recurring instructions and preferences
3. **Leverage slash commands**: Create shortcuts for common workflows
4. **Configure permissions**: Restrict access to sensitive areas when appropriate

### Development Workflow
1. **Start broad, then narrow**: Begin with understanding, then specific implementation
2. **Review changes**: Always check generated code before accepting
3. **Run tests**: Verify changes don't break existing functionality
4. **Commit frequently**: Use Claude's Git integration for clean commit history

### Security Considerations
1. **Never commit secrets**: Claude follows security best practices but always verify
2. **Review file permissions**: Ensure Claude can only access necessary files
3. **Use local settings**: Keep sensitive configuration in `.local.json` files
4. **Regular updates**: Keep Claude Code updated for latest security patches

### Performance Tips
1. **Use specific file patterns**: Help Claude focus on relevant code
2. **Leverage specialized agents**: Use subagents for complex tasks
3. **Batch related changes**: Group similar edits together
4. **Clear context when needed**: Use `/clear` for unrelated new tasks

---

For additional help and support:
- Use `/help` within Claude Code
- Visit the official documentation at https://docs.anthropic.com/en/docs/claude-code
- Report issues at https://github.com/anthropics/claude-code/issues