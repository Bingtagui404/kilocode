---
title: "The Chat Interface"
description: "Learn how to use the Kilo Code chat interface effectively"
---

# Chatting with Kilo Code

{% callout type="tip" %}
**Bottom line:** Kilo Code is an AI coding assistant you chat with in plain English. It writes, edits, and explains code for you.
{% /callout %}

{% callout type="note" title="Prefer quick completions?" %}
If you're typing code in the editor and want AI to finish your line or block, check out [Autocomplete](/docs/code-with-ai/features/autocomplete) instead. Chat is best for larger tasks, explanations, and multi-file changes.
{% /callout %}

## Quick Setup

{% tabs %}
{% tab label="Classic Extension" %}

Find the Kilo Code icon ({% kilo-code-icon /%}) in VS Code's Primary Side Bar. Click it to open the chat panel.

**Lost the panel?** Go to View > Open View... and search for "Kilo Code"

{% /tab %}
{% tab label="New Extension" %}

Click the Kilo Code icon ({% kilo-code-icon /%}) in VS Code's Primary Side Bar to open the sidebar chat. You can also pop it out into an editor tab for a larger workspace.

{% /tab %}
{% tab label="CLI" %}

Open your terminal and run `kilo` to launch the interactive TUI. You'll see a prompt where you can start typing requests immediately. The TUI is fully keyboard-driven — no mouse required.

{% /tab %}
{% /tabs %}

## How to Talk to Kilo Code

**The key insight:** Just type what you want in normal English. No special commands needed.

{% image src="/docs/img/typing-your-requests/typing-your-requests.png" alt="Example of typing a request in Kilo Code" width="800" caption="Example of typing a request in Kilo Code" /%}

**Good requests:**

- `create a new file named utils.py and add a function called add that takes two numbers as arguments and returns their sum`
- `in the file @src/components/Button.tsx, change the color of the button to blue`
- `find all instances of the variable oldValue in @/src/App.js and replace them with newValue`

**What makes requests work:**

- **Be specific** - "Fix the bug in `calculateTotal` that returns incorrect results" beats "Fix the code"
- **Reference files** - Point Kilo to the files you're working with
- **One task at a time** - Break complex work into manageable steps
- **Include examples** - Show the style or format you want

{% callout type="info" title="Chat vs Autocomplete" %}
**Use chat** when you need to describe what you want, ask questions, or make changes across multiple files.

**Use [autocomplete](/docs/code-with-ai/features/autocomplete)** when you're already typing code and want the AI to finish your thought inline.
{% /callout %}

## The Chat Interface

{% tabs %}
{% tab label="Classic Extension" %}

{% image src="/docs/img/the-chat-interface/the-chat-interface-1.png" alt="Chat interface components labeled with callouts" width="800" caption="Everything you need is right here" /%}

**Essential controls:**

- **Chat history** - See your conversation and task history
- **Input field** - Type your requests here (press Enter to send)
- **Action buttons** - Approve or reject Kilo's proposed changes
- **Plus button** - Start a new task session
- **Mode selector** - Choose how Kilo should approach your task

**Providing context with @-mentions:**

Reference files and other context directly in your message using `@`:

- `@file` - Reference a specific file
- `@url` - Include content from a URL
- `@problems` - Include current VS Code problems
- `@terminal` - Include terminal output
- `@git-changes` - Include uncommitted changes
- `@commit` - Reference a specific commit

{% /tab %}
{% tab label="New Extension" %}

**Essential controls:**

- **Input prompt** - Type your requests and press Enter to send
- **Action buttons** - Approve or reject proposed changes
- **Agent dropdown** - Switch between agents (e.g. Code, Ask, Plan) from the sidebar
- **Session management** - Start new sessions or resume previous ones

**Providing context:**

The extension automatically passes context from your editor, including your open tabs, active file, selection, and diagnostics. You can also reference file paths directly in your message — no special `@` syntax required. Just mention the path naturally, like "update src/utils.ts to add a helper function."

{% /tab %}
{% tab label="CLI" %}

**Essential controls:**

- **Input prompt** - Type your requests and press Enter to send
- **Action buttons** - Approve or reject proposed changes
- **Agent cycling** - Switch between agents using keybinds or slash commands
- **Session management** - Start new sessions or resume previous ones

**Providing context:**

Mention file paths directly in your message (e.g., "look at src/utils.ts") and the agent will read them. You can also use the `--file` flag when starting a session to explicitly include files. The agent has `glob`, `grep`, and `read` tools to discover files on its own.

{% /tab %}
{% /tabs %}

## Quick Interactions

**Click to act:**

- File paths → Opens the file
- URLs → Opens in browser
- Messages → Expand/collapse details
- Code blocks → Copy button appears

**Status signals:**

- Spinning → Kilo is working
- Red → Error occurred
- Green → Success

## Common Mistakes to Avoid

| Instead of this...                | Try this                                                                            |
| --------------------------------- | ----------------------------------------------------------------------------------- |
| "Fix the code"                    | "Fix the bug in `calculateTotal` that returns incorrect results"                    |
| Assuming Kilo knows context       | Reference specific files so Kilo knows where to look                                |
| Multiple unrelated tasks          | Submit one focused request at a time                                                |
| Technical jargon overload         | Clear, straightforward language works best                                          |
| Using chat for tiny code changes. | Use [autocomplete](/docs/code-with-ai/features/autocomplete) for inline completions |

**Why it matters:** Kilo Code works best when you communicate like you're talking to a smart teammate who needs clear direction.

## Suggested Responses

When Kilo Code needs more information to complete a task, it uses the [`ask_followup_question`](/docs/automate/tools/ask-followup-question) tool. To make responding easier and faster, Kilo Code often provides suggested answers alongside the question.

{% tabs %}
{% tab label="Classic Extension" %}

{% image src="/docs/img/suggested-responses/suggested-responses.png" alt="Example of Kilo Code asking a question with suggested response buttons below it" width="800" caption="Suggested responses appear as clickable buttons below questions" /%}

**How it works:**

1. **Question Appears** - Kilo Code asks a question using the `ask_followup_question` tool
2. **Suggestions Displayed** - Suggested answers appear as clickable buttons below the question
3. **Interaction** - You can interact with these suggestions in two ways:
   - **Click** a button to send that answer immediately
   - **Shift+Click** (or click the pencil icon {% codicon name="edit" /%}) to copy the suggestion into the input field so you can edit it before sending

{% /tab %}
{% tab label="New Extension & CLI" %}

**How it works:**

1. **Question Appears** - Kilo Code asks a question using the `question` tool
2. **Options Displayed** - Selectable options are presented that you can choose from
3. **Selection** - Pick an option or type a custom response

{% /tab %}
{% /tabs %}

**Benefits:**

- **Speed** - Quickly respond without typing full answers
- **Clarity** - Suggestions often clarify the type of information Kilo Code needs
- **Flexibility** - Edit suggestions to provide precise, customized answers when needed

## Tips for Better Workflow

{% tabs %}
{% tab label="Classic Extension" %}

{% callout type="tip" %}
**Move Kilo Code to the Secondary Side Bar** for a better layout. Right-click on the Kilo Code icon in the Activity Bar and select **Move To → Secondary Side Bar**. This lets you see the Explorer, Search, Source Control, etc. alongside Kilo Code.

{% image src="/docs/img/move-to-secondary.png" alt="Move to Secondary Side Bar" width="600" caption="Move Kilo Code to the Secondary Side Bar for better workspace organization" /%}
{% /callout %}

{% callout type="tip" %}
**Drag files directly into chat.** Once you have Kilo Code in a separate sidebar from the file explorer, you can drag files from the explorer into the chat window (even multiple at once). Just hold down the Shift key after you start dragging the files.
{% /callout %}

{% /tab %}
{% tab label="New Extension" %}

{% callout type="tip" %}
**Use agents instead of modes.** Switch between agents like Code, Ask, and Plan using the agent dropdown or slash commands. Each agent is tuned for a different type of task.
{% /callout %}

{% callout type="tip" %}
**Your editor context is automatic.** The extension reads your open tabs, active file, selection, and diagnostics, so you don't need to manually reference every file. Focus your message on what you want done.
{% /callout %}

{% callout type="tip" %}
**Pop out to an editor tab.** If the sidebar feels cramped, pop the chat into a full editor tab for more room.
{% /callout %}

{% /tab %}
{% tab label="CLI" %}

{% callout type="tip" %}
**Use agents instead of modes.** Switch between agents like Code, Ask, and Plan using keybinds or slash commands. Each agent is tuned for a different type of task.
{% /callout %}

{% callout type="tip" %}
**The TUI is keyboard-driven.** Navigate, approve changes, and switch agents entirely from the keyboard — no mouse needed.
{% /callout %}

{% /tab %}
{% /tabs %}

Ready to start coding? Open the chat and describe what you want to build!
