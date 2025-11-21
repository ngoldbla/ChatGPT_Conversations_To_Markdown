# The Parley - ChatGPT Data Migration Tool

Transform your exported ChatGPT conversations into beautifully formatted Markdown files optimized for BYOK (Bring Your Own Key) applications like Cherry Studio and other knowledge base tools.

**Two ways to use this tool:**
- 🌐 **Browser-Based Tool** (Recommended) - Easy, no installation required
- 💻 **Python Scripts** - For terminal users who prefer command-line tools

Both handle the complete ChatGPT export including conversations, images, DALL-E generations, and all attachments.

## 🚀 Quick Start (Recommended)

### Browser-Based Migration Tool (No Installation!)

**[📥 Download the-parley.html](https://raw.githubusercontent.com/daugaard47/ChatGPT_Conversations_To_Markdown/main/the-parley.html)** *(Right-click → Save As)*

**Then:**

1. **Open** the downloaded HTML file in your browser (Chrome, Firefox, Safari, Edge - all work!)
2. **Follow** the three-step guided workflow:
   - **Step 1**: Instructions for exporting from ChatGPT
   - **Step 2**: Upload ZIP and configure conversion
   - **Step 3**: Import into Cherry Studio or your BYOK app

That's it! No Python, no terminal, no dependencies. Everything runs locally in your browser.

> 💡 **Privacy First**: All processing happens in your browser. Your conversations never leave your computer.

---

## 🎯 The Complete Migration Workflow

### Step 1: Export Your ChatGPT Data

1. Go to [ChatGPT Settings](https://chatgpt.com/settings) → **Data Controls**
2. Click **"Export data"**
3. Wait for the email from OpenAI (usually arrives within a few hours)
4. Download the ZIP file from the email
5. **Keep the ZIP file** - no need to extract!

### Step 2: Convert to Markdown

Upload your ChatGPT export ZIP file to The Parley converter:
- Configure your preferences (name, organization mode, formatting)
- All processing happens in your browser (nothing uploaded!)
- Download your organized markdown files

### Step 3: Import into Your BYOK App

#### Cherry Studio Knowledge Base Setup

**Prerequisites:**
- Cherry Studio installed
- OpenAI API key

**Setup Instructions:**

1. **Add OpenAI Embeddings Model**
   - Open Cherry Studio → Settings → Models
   - Add new model:
     - Provider: OpenAI
     - Model Name: `text-embedding-3-large`
     - API Key: Your OpenAI API key

2. **Create Knowledge Base**
   - Navigate to Knowledge Base in Cherry Studio
   - Create New Knowledge Base
   - Name it (e.g., "My ChatGPT Conversations")
   - Select **MinerU** as the document processor
   - Select **text-embedding-3-large** as the embeddings model
   - Import your markdown files from the `MarkdownFiles` folder
   - Wait for processing to complete

3. **Use Your Knowledge Base**
   - Search through all your ChatGPT conversations
   - Ask questions about past conversations
   - Get AI-powered insights from your history
   - Reference specific conversations in new chats

**Learn More:** [Cherry Studio Knowledge Base Documentation](https://docs.cherry-ai.com/docs/en-us/knowledge-base/knowledge-base)

#### Other BYOK Applications

The Parley outputs standard markdown files that work with any BYOK application supporting:
- Markdown document import
- Knowledge base / RAG functionality
- Custom embeddings models

Check your app's documentation for specific import instructions.

---

## ✨ Features

### Core Functionality
* **Complete ChatGPT Export Processing** - Handles the entire ChatGPT data export including all files and folders
* **Multimodal Content Support** - Automatically extracts and embeds images, screenshots, and attachments
* **DALL-E Image Organization** - Separate handling for AI-generated images
* **Smart File Organization** - Creates conversation-specific folders for all attachments

### Message Format Support
* **Regular Messages** - Standard user and assistant conversations
* **Audio Messages** - Voice conversations embedded with HTML5 audio players
* **Internal Reasoning** - ChatGPT's thinking process with special formatting
* **Reasoning Summaries** - Brief reasoning recaps
* **Tool Calls & Execution** - ChatGPT tool usage tracking
* **Tool Results** - External tool response messages
* **User Context** - Profile and instruction context
* **Code Blocks** - Properly formatted code with syntax highlighting support

### Knowledge Base Optimization
* **YAML Frontmatter** - Searchable metadata with title, creation date, update date, and tags
* **Collapsible Sections** - HTML details for special content types
* **Embedded Images** - Relative paths for portability
* **Cross-Platform Compatibility** - Works on Windows, macOS, and Linux

### Customization Options
* Customize user and assistant display names
* Toggle YAML frontmatter and collapsible sections
* Include or exclude conversation dates
* Custom date formatting
* Custom filename templates
* Configurable message separators
* Skip empty messages option

---

## 💻 Python Scripts (Alternative Method)

**For users who prefer terminal/command-line tools:**

### Prerequisites

* Python 3.7 or higher
* ChatGPT data export (see Step 1 above)

### Installation

**One-Command Install:**

**Windows:**
```batch
curl -sL https://raw.githubusercontent.com/daugaard47/ChatGPT_Conversations_To_Markdown/main/install.bat -o install.bat && install.bat
```

**Mac/Linux:**
```bash
curl -sL https://raw.githubusercontent.com/daugaard47/ChatGPT_Conversations_To_Markdown/main/install.sh | bash
```

**OR Manual Installation:**

```bash
git clone https://github.com/daugaard47/ChatGPT_Conversations_To_Markdown.git
cd ChatGPT_Conversations_To_Markdown
pip install -r requirements.txt
```

### Python Usage

1. **Run setup wizard** (first time only):
```bash
python setup.py
```

2. **Convert conversations**:
```bash
python chatgpt_json_to_markdown.py
```

3. **Done!** Open your `MarkdownFiles` folder

### What Happens During Conversion

Both methods will:
- ✅ Process all your conversations (could be 100s!)
- ✅ Organize by your chosen mode (flat/category/date/hybrid)
- ✅ Copy and organize all images → `Assets/Images/`
- ✅ Copy and embed all audio → `Assets/Audio/`
- ✅ Separate DALL-E images → `Assets/DALLE/`
- ✅ Create markdown files with embedded media
- ✅ Generate YAML frontmatter for knowledge bases
- ✅ Show progress during processing

---

## 📁 Output Structure

The tool supports **4 organization modes** (choose during setup):

### Hybrid Mode (RECOMMENDED) ⭐

```
MarkdownFiles/
├── Assets/
│   ├── Images/        (all screenshots, uploaded images)
│   ├── Audio/         (all voice conversations)
│   └── DALLE/         (AI-generated images)
├── Starred/
│   └── 2025/
│       ├── 01-January/
│       └── 02-February/
├── Archived/
│   └── 2025/
│       └── 01-January/
└── Regular/
    └── 2025/
        ├── 01-January/
        ├── 02-February/
        └── 03-March/
```

**Other modes:** See the [Organization Guide](ORGANIZATION.md) for Flat, By Category, and By Date modes.

**Media Embedding:**
- Images: `![Image](../../Assets/Images/file-ABC123.png)`
- Audio: `[🎵 Audio (11.3s)](../../Assets/Audio/file_0000.wav)`

---

## 📝 Example Output

```markdown
---
title: "My Conversation About React"
created: 2025-01-15 14:30:00
updated: 2025-01-15 16:45:00
tags:
  - chatgpt
  - conversation
---

# My Conversation About React

<sub>01-15-2025</sub>

---

**User**:

Can you help me understand React hooks?

**ChatGPT**:

Of course! React hooks are functions that let you use state...

**User**:

![Image](Assets/file-ABC123-diagram.png)

Can you explain this diagram?

<details><summary>💭 Internal Reasoning</summary>

**Analyzing diagram**: The user has shared a component lifecycle diagram...

</details>

**ChatGPT**:

This diagram shows the React component lifecycle...
```

---

## 🔧 Troubleshooting

### Missing Images
- Make sure you extracted **ALL files** from the ChatGPT export ZIP (or use the browser tool which handles this automatically)
- Verify that `file-*` files and folders are in the `JsonFiles` directory
- Check that paths in `config.json` are absolute paths (e.g., `C:\Users\...` on Windows)

### Path Errors on Windows
- Use double backslashes in paths: `C:\\Users\\...`
- Or use forward slashes: `C:/Users/...`

### Virtual Environment Issues (Python only)
```bash
# Deactivate and recreate if needed
deactivate
rm -rf venv  # or rmdir /s venv on Windows
python -m venv venv
venv\Scripts\activate  # Windows
pip install tqdm
```

---

## 📊 What Gets Converted?

✅ **Included:**
- All conversation text
- Images and screenshots you uploaded
- DALL-E generated images
- **Audio messages** - Embedded with playable links
- Tool calls and execution logs
- ChatGPT's internal reasoning (if available)
- User context and custom instructions
- Code blocks with formatting

⚠️ **Special Handling:**
- Video messages are shown as links (audio track not currently extracted)
- ChatGPT's web browsing results show content but not raw data

---

## 🤝 Contributing

**This is a free and open-source project!** Contributions are not just welcome - they're encouraged.

### Ways to Contribute:

- 🐛 **Report bugs** - Open an issue if something doesn't work
- 💡 **Suggest features** - Tell us what would make this better
- 🔧 **Submit pull requests** - Fix bugs, add features, improve docs
- 📖 **Improve documentation** - Help others understand how to use this
- ⭐ **Star the repo** - Show your support!

### Pull Request Guidelines:

1. **Test your changes** - Make sure both HTML and Python versions work
2. **Update README** - Document new features
3. **Keep it simple** - This tool is meant to be easy to use
4. **Follow existing patterns** - Match the current code style

**Not sure where to start?** Check the [Issues](https://github.com/daugaard47/ChatGPT_Conversations_To_Markdown/issues) page for ideas or open a new discussion!

---

## 📄 License

This project is **free and open source**, available under the MIT License.

You can:
- ✅ Use it for personal projects
- ✅ Use it for commercial projects
- ✅ Modify and distribute it
- ✅ Build upon it

**No attribution required** (but appreciated!)

---

## 📞 Support & Questions

**Need help?**
- 📖 Check the [Troubleshooting](#-troubleshooting) section above
- 🐛 [Open an issue](https://github.com/daugaard47/ChatGPT_Conversations_To_Markdown/issues) on GitHub
- 💬 Start a [Discussion](https://github.com/daugaard47/ChatGPT_Conversations_To_Markdown/discussions) for questions

**Found a bug or have an idea?** We'd love to hear from you! This project gets better with community input.

---

## 🙏 Acknowledgments

- The Parley is built on the ChatGPT Conversations to Markdown project
- Created with help from the community
- Supports ChatGPT multimodal content and knowledge base optimization

---

## ⭐ Show Your Support

If this tool helped you migrate your ChatGPT conversations:
- ⭐ **Star this repo** on GitHub
- 🐛 **Report bugs** to help improve it
- 💡 **Share your ideas** for new features
- 🔧 **Contribute code** if you're a developer
- 📢 **Tell others** who might find it useful

---

**Enjoy seamless ChatGPT data migration with The Parley!** 🎉

*Free, open source, and privacy-focused.*
