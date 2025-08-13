
# GitHub Copilot Mode Pack

A curated collection of custom GitHub Copilot chat modes designed to enhance your development workflow with specialized AI assistants for different scenarios.

## 🎯 What's Inside

- **Tutor Mode** - Educational assistant that teaches concepts and guides learning without providing complete solutions
- **Assist Mode** - Development assistant for handling boilerplate, setup tasks, documentation, and tedious implementation work
- **Hands-Off Mode** - Full-control AI engineer for complete feature implementation with built-in quality and safety guardrails

## 🚀 Setup Instructions

### Method 1: Global Setup (All Workspaces)

1. Open VS Code with GitHub Copilot extension installed
2. Open GitHub Copilot Chat panel
3. In the mode selector area (where you see Ask, Agent, Edit), click "Configure modes"
4. This opens your user data folder for chat modes
5. Create a new `.chatmode.md` file (e.g., `Assist.chatmode.md`)
6. Copy the content from one of the mode files in this repo
7. Save the file - the mode will appear in your mode selector

### Method 2: Workspace-Specific Setup

1. Create a `.github/chatmodes/` folder in your project root
2. Copy the desired `.chatmode.md` files into this folder
3. The modes will only be available for that specific workspace
4. Restart VS Code or reload the window to see the new modes

## 💡 Usage Tips

- **Tutor Mode**: Best for learning new technologies, understanding complex concepts, and developing problem-solving skills through guided explanations
- **Assist Mode**: Perfect for generating boilerplate code, documentation, configs, and handling repetitive implementation tasks
- **Hands-Off Mode**: Ideal for full-vibe coding sessions where you want the AI to take complete control with built-in safety guardrails and code quality enforcement

## 🔧 Mode Selection

Once installed, simply select your desired mode from the dropdown in the Copilot Chat panel instead of the default Ask/Agent/Edit modes.

## 🤝 Contributing

Feel free to submit new modes or improvements to existing ones via pull requests!

---

*Enhance your coding experience with purpose-built AI assistants* ✨
