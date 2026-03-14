---
title: "Using Modes"
description: "Understanding and using different modes (agents) in Kilo Code"
---

# Using Modes

Modes in Kilo Code are specialized personas that tailor the assistant's behavior to your current task. Each mode offers different capabilities, expertise, and access levels to help you accomplish specific goals.

{% callout type="info" %}
The Classic Extension calls these **modes**, while the New Extension and CLI call them **agents**. The concept is the same—specialized personas with distinct tool access and behavior.
{% /callout %}

## Why Use Different Modes?

- **Task specialization:** Get precisely the type of assistance you need for your current task
- **Safety controls:** Prevent unintended file modifications when focusing on planning or learning
- **Focused interactions:** Receive responses optimized for your current activity
- **Workflow optimization:** Seamlessly transition between planning, implementing, debugging, and learning

## Switching Between Modes

{% tabs %}
{% tab label="Classic Extension" %}

{% youtube url="https://youtu.be/cS4vQfX528w" caption="Explaining the different modes in Kilo Code" /%}

Four ways to switch modes:

1. **Dropdown menu:** Click the selector to the left of the chat input

   {% image src="/docs/img/modes/modes.png" alt="Using the dropdown menu to switch modes" width="400" /%}

2. **Slash command:** Type `/code`, `/architect`, `/ask`, or `/debug` in the chat input to switch modes. Type `/newtask` to create a new task, or `/smol` to condense your context window.

   {% image src="/docs/img/modes/modes-1.png" alt="Using slash commands to switch modes" width="400" /%}

#### Understanding /newtask vs /smol

| Command    | Purpose                                               | When to Use                                                             |
| ---------- | ----------------------------------------------------- | ----------------------------------------------------------------------- |
| `/newtask` | Creates a new task with context from the current task | When you want to start something new while carrying over context        |
| `/smol`    | Condenses your current context window                 | When your conversation is getting too long and you want to summarize it |

3. **Keyboard shortcut:** Each press cycles through available modes in sequence.

   | Operating System | Shortcut |
   | ---------------- | -------- |
   | macOS            | ⌘ + .    |
   | Windows          | Ctrl + . |
   | Linux            | Ctrl + . |

4. **Accept suggestions:** Click on mode switch suggestions that Kilo Code offers when appropriate

   {% image src="/docs/img/modes/modes-2.png" alt="Accepting a mode switch suggestion from Kilo Code" width="400" /%}

{% /tab %}
{% tab label="New Extension" %}

There are several ways to switch agents:

- **Dropdown menu:** Click the agent selector in the sidebar to switch between agents.
- **Slash commands:** Type `/` in the chat input to switch agents (e.g., `/code`, `/ask`, `/plan`, `/debug`).
- **Keyboard shortcut:** Use a keyboard shortcut to cycle through available agents.

{% /tab %}
{% tab label="CLI" %}

There are several ways to switch agents:

- **Keybinds:** Press the displayed key to cycle through available agents.
- **Slash commands:** Type `/` in the chat input to see available commands, including switching agents (e.g., `/code`, `/ask`, `/plan`, `/debug`).
- **Config file:** Set the `default_agent` key in your configuration to change the default agent on startup.

{% /tab %}
{% /tabs %}

## Built-in Modes

{% tabs %}
{% tab label="Classic Extension" %}

### Code Mode (Default)

| Aspect               | Details                                                                                                  |
| -------------------- | -------------------------------------------------------------------------------------------------------- |
| **Description**      | A skilled software engineer with expertise in programming languages, design patterns, and best practices |
| **Tool Access**      | Full access to all tool groups: `read`, `edit`, `browser`, `command`, `mcp`                              |
| **Ideal For**        | Writing code, implementing features, debugging, and general development                                  |
| **Special Features** | No tool restrictions—full flexibility for all coding tasks                                               |

### Ask Mode

| Aspect               | Details                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| **Description**      | A knowledgeable technical assistant focused on answering questions without changing your codebase |
| **Tool Access**      | Limited access: `read`, `browser`, `mcp` only (cannot edit files or run commands)                 |
| **Ideal For**        | Code explanation, concept exploration, and technical learning                                     |
| **Special Features** | Optimized for informative responses without modifying your project                                |

### Architect Mode

| Aspect               | Details                                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------------------- |
| **Description**      | An experienced technical leader and planner who helps design systems and create implementation plans |
| **Tool Access**      | Access to `read`, `browser`, `mcp`, and restricted `edit` (markdown files only)                      |
| **Ideal For**        | System design, high-level planning, and architecture discussions                                     |
| **Special Features** | Follows a structured approach from information gathering to detailed planning                        |

### Debug Mode

| Aspect               | Details                                                                             |
| -------------------- | ----------------------------------------------------------------------------------- |
| **Description**      | An expert problem solver specializing in systematic troubleshooting and diagnostics |
| **Tool Access**      | Full access to all tool groups: `read`, `edit`, `browser`, `command`, `mcp`         |
| **Ideal For**        | Tracking down bugs, diagnosing errors, and resolving complex issues                 |
| **Special Features** | Uses a methodical approach of analyzing, narrowing possibilities, and fixing issues |

{% callout type="tip" %}
**Keep debugging separate from main tasks:** When using Debug mode, ask Kilo to "start a new task in Debug mode with all of the necessary context needed to figure out X" so that the debugging process uses its own context window and doesn't pollute the main task.
{% /callout %}

### Orchestrator Mode

| Aspect               | Details                                                                                                             |
| -------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Description**      | A strategic workflow orchestrator who coordinates complex tasks by delegating them to appropriate specialized modes |
| **Tool Access**      | Limited access to create new tasks and coordinate workflows                                                         |
| **Ideal For**        | Breaking down complex projects into manageable subtasks assigned to specialized modes                               |
| **Special Features** | Uses the new_task tool to delegate work to other modes                                                              |

### Review Mode

| Aspect               | Details                                                                                                                           |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Description**      | An expert code reviewer specializing in analyzing changes to provide structured feedback on quality, security, and best practices |
| **Tool Access**      | Access to `read`, `browser`, `mcp`, and when permitted, `edit`                                                                    |
| **Ideal For**        | Catching issues early, enforcing code standards, accelerating PR turnaround                                                       |
| **Special Features** | Code review before committing, surfacing feedback across performance, security, style, and test coverage                          |

{% /tab %}
{% tab label="New Extension & CLI" %}

### code (Default)

| Aspect               | Details                                                                                                  |
| -------------------- | -------------------------------------------------------------------------------------------------------- |
| **Description**      | A skilled software engineer with expertise in programming languages, design patterns, and best practices |
| **Tool Access**      | Full access to all tools: `read`, `edit`, `glob`, `grep`, `bash`, `task`, `webfetch`, `mcp`, etc.        |
| **Ideal For**        | Writing code, implementing features, debugging, and general development                                  |
| **Special Features** | No tool restrictions—full flexibility for all coding tasks                                               |

### ask

| Aspect               | Details                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| **Description**      | A knowledgeable technical assistant focused on answering questions without changing your codebase |
| **Tool Access**      | Read-only tools only (cannot edit files or run commands)                                          |
| **Ideal For**        | Code explanation, concept exploration, and technical learning                                     |
| **Special Features** | Optimized for informative responses without modifying your project                                |

### plan

| Aspect               | Details                                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------------------- |
| **Description**      | An experienced technical leader and planner who helps design systems and create implementation plans |
| **Tool Access**      | Read-only tools plus restricted file editing (e.g., markdown files only)                             |
| **Ideal For**        | System design, high-level planning, and architecture discussions                                     |
| **Special Features** | Replaces the Classic Extension's "Architect" mode with similar planning-focused behavior             |

### debug

| Aspect               | Details                                                                             |
| -------------------- | ----------------------------------------------------------------------------------- |
| **Description**      | An expert problem solver specializing in systematic troubleshooting and diagnostics |
| **Tool Access**      | Full access to all tools                                                            |
| **Ideal For**        | Tracking down bugs, diagnosing errors, and resolving complex issues                 |
| **Special Features** | Uses a methodical approach of analyzing, narrowing possibilities, and fixing issues |

### orchestrator

| Aspect               | Details                                                                                                              |
| -------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **Description**      | A strategic workflow orchestrator who coordinates complex tasks by delegating them to appropriate specialized agents |
| **Tool Access**      | Limited access to create new tasks and coordinate workflows                                                          |
| **Ideal For**        | Breaking down complex projects into manageable subtasks assigned to specialized agents                               |
| **Special Features** | Delegates work to other agents; also has access to the **explore** subagent for codebase exploration                 |

{% callout type="info" %}
The New Extension and CLI do not include a built-in Review agent. Code review workflows can be handled by the **code** agent or via custom agent configurations.
{% /callout %}

{% /tab %}
{% /tabs %}

## Custom Modes

Create your own specialized assistants by defining tool access, file permissions, and behavior instructions. Custom modes help enforce team standards or create purpose-specific assistants. See [Custom Modes documentation](/docs/customize/custom-modes) for setup instructions.
