# 🤖 AgentUse PR Review Agent

AI-powered pull request automation you can actually read and customize.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## ✨ Features

- **🔍 Automatic Code Review** - Reviews PRs on open/update
- **💬 Comment Replies** - Mention `@agentuse` to ask questions
- **✏️ Fully Customizable** - Edit prompts to match your team's standards
- **🤖 Any Model** - Claude, GPT, or open-source (GLM, MiniMax) via [OpenRouter](https://openrouter.ai/models)
- **🔓 No Vendor Lock-in** - Your prompts, your API keys, your control

## 🚀 Quick Start

### 1. Copy to your repo

```bash
# Clone this repo's .github folder to your project
cp -r .github/agents .github/workflows your-project/.github/
```

### 2. Add your API key

Go to **Settings → Secrets → Actions** and add one of:

| Secret | Provider | Best For |
|--------|----------|----------|
| `ANTHROPIC_API_KEY` | [Anthropic Console](https://console.anthropic.com) | Pay-per-use |
| `OPENAI_API_KEY` | [OpenAI](https://platform.openai.com) | GPT models |
| `OPENROUTER_API_KEY` | [OpenRouter](https://openrouter.ai) | Multiple providers |

<details>
<summary>💡 <strong>Using Claude Pro/Max subscription (recommended)</strong></summary>

```bash
npx agentuse auth setup-github
```

</details>

### 3. Done!

Open a PR and watch the magic happen.

---

## 📁 What's Inside

```
.github/
├── workflows/
│   ├── agentuse-code-review.yml    # PR review workflow
│   └── agentuse-comment-reply.yml  # Comment reply workflow
└── agents/
    ├── code-review.agentuse        # PR review agent
    └── comment-reply.agentuse      # Comment reply agent
```

## 🎨 Customization

The agents are just text files. Edit them to fit your needs:

```bash
# Review focus areas, output format, etc.
vim .github/agents/code-review.agentuse
```

### Example: Add custom review criteria

```yaml
### 2.7 My Custom Check
- Check for our internal patterns
- Verify feature flags usage
- etc.
```

---

## 💬 Usage

### Automatic Review

Every PR gets reviewed automatically:

```
## 🔍 Code Review Summary

| Files Changed | Additions | Deletions |
|---------------|-----------|-----------|
| 5             | +120      | -30       |

### 📋 Overview
This PR adds user authentication...

### 🔎 Findings
...
```

### Ask Questions

Comment on any PR with `@agentuse`:

```
@agentuse explain what this function does
@agentuse are there any security concerns?
@agentuse suggest improvements for performance
```

---

## 🔧 Configuration

### Change the model

Edit `.github/agents/code-review.agentuse`:

```yaml
---
model: anthropic:claude-sonnet-4-5  # or openai:gpt-4o, openrouter:z-ai/glm-4.7
---
```

### Disable automatic reviews

Remove the `pull_request` trigger in `.github/workflows/agentuse.yml`:

```yaml
on:
  # pull_request:  # Comment out to disable
  issue_comment:
    types: [created]
```

---

## 📚 Resources

- [AgentUse Documentation](https://docs.agentuse.io)
- [AgentUse GitHub](https://github.com/agentuse/agentuse)
- [Agent File Format](https://docs.agentuse.io/agents)

---

## 📄 License

MIT - Do whatever you want with it.
