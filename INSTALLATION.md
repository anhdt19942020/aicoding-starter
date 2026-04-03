# Installation Guide — Codex CLI Setup

Complete step-by-step guide to install and configure OpenAI Codex CLI.

---

## Prerequisites

Before installing Codex CLI, verify you have:

- ✅ **OpenAI Account** → https://platform.openai.com
- ✅ **API Key** → https://platform.openai.com/api-keys
- ✅ **Terminal/CLI Experience** — Comfortable with command line
- ✅ **Git Installed** — For version control
- ✅ **Code Editor** — VS Code, Cursor, or similar

---

## Step 1: Get OpenAI API Key

### Create API Key
1. Go to https://platform.openai.com/api-keys
2. Click "Create new secret key"
3. Name it: "Codex CLI" (or your preference)
4. Copy and save securely (don't share!)

### Store API Key Safely
```bash
# macOS/Linux:
echo 'export OPENAI_API_KEY="your-key-here"' >> ~/.bashrc
source ~/.bashrc

# Windows (PowerShell as Admin):
[Environment]::SetEnvironmentVariable("OPENAI_API_KEY", "your-key-here", "User")
# Restart PowerShell for changes to take effect

# Verify (all platforms):
echo $OPENAI_API_KEY
# Should output: your-key-here
```

---

## Step 2: Install Codex CLI

### Option A: macOS (Recommended)
```bash
# Using Homebrew
brew install openai-codex

# Verify installation
codex --version

# Initialize config
mkdir -p ~/.codex
# Configuration will auto-create on first use
```

### Option B: Windows

#### Via NPM (Recommended for Windows)
```powershell
# Using Node.js/NPM
npm install -g @openai/codex

# Verify installation
codex --version

# Initialize config
mkdir -p $env:USERPROFILE\.codex
# Configuration will auto-create on first use
```

#### Via Chocolatey
```powershell
# If you have Chocolatey installed
choco install openai-codex

# Verify
codex --version
```

### Option C: Linux

#### Ubuntu/Debian
```bash
# Using apt (if available)
apt-get install openai-codex

# Or via NPM (universal)
npm install -g @openai/codex

# Verify
codex --version
```

#### Via NPM (Universal, All Linux Distros)
```bash
# Install Node.js first if not installed
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Install Codex
npm install -g @openai/codex

# Verify
codex --version
```

### Option D: Docker (Advanced)
```bash
# Create Dockerfile
FROM node:18-alpine
RUN npm install -g @openai/codex
ENTRYPOINT ["codex"]
CMD ["--help"]

# Build image
docker build -t codex-cli .

# Run container
docker run -e OPENAI_API_KEY=$OPENAI_API_KEY codex-cli start
```

---

## Step 3: Configure Codex CLI

### Initialize Configuration
```bash
# Create config directory
mkdir -p ~/.codex

# Codex will auto-create config.toml on first use
# Or manually create:
touch ~/.codex/config.toml
```

### Setup Config File

**Location:** `~/.codex/config.toml`

```toml
# Basic Configuration
model = "gpt-4o"              # or "o3", "o4-mini"

[context]
project_doc_max_bytes = 65536  # 64KB for AGENTS.md

[behavior]
auto_compact = true            # Auto-compact long sessions
session_timeout = "7d"

[output]
format = "text"
show_reasoning = false         # true = show o3 reasoning
```

### Verify Configuration
```bash
# Test connection to OpenAI
codex start

# You should see:
# "Starting new session..."
# "Ready for input"

# Exit (press Ctrl+C)
```

---

## Step 4: Download This Repository

### Clone Codex-Howto
```bash
# Clone repository
git clone https://github.com/yourusername/codex-howto
cd codex-howto

# Or download as ZIP
# https://github.com/yourusername/codex-howto/archive/refs/heads/main.zip
```

### Copy Global Instructions
```bash
# Copy AGENTS.md to Codex home
cp AGENTS.md ~/.codex/AGENTS.md

# Verify
cat ~/.codex/AGENTS.md | head -20
```

---

## Step 5: Setup Your First Project

### Choose Template
```bash
# Option 1: Laravel API
cp -r templates/laravel-project ~/my-api

# Option 2: NestJS API
cp -r templates/nestjs-project ~/my-api

# Option 3: Next.js App
cp -r templates/nextjs-project ~/my-app
```

### Customize AGENTS.md
```bash
cd ~/my-api

# Edit AGENTS.md with your editor
# Update:
# - Project name
# - Project path
# - Port numbers
# - Your specific domains
# - Code examples

nano AGENTS.md
# or
code AGENTS.md
# or
vim AGENTS.md
```

### Initialize Git
```bash
# If not already a git repo
git init

# Add AGENTS.md to version control
git add AGENTS.md

# Exclude local Codex files
echo ".codex/" >> .git/info/exclude

# Commit
git commit -m "docs: Add Codex project instructions"
```

---

## Step 6: Start Using Codex

### First Session
```bash
# Navigate to project
cd ~/my-api

# Start Codex
codex start

# Codex will:
# 1. Load AGENTS.md automatically
# 2. Initialize session with context
# 3. Show ready prompt

# You can now ask:
# "Create a new API endpoint for payments"
# "Generate tests for this service"
# etc.
```

### Daily Usage
```bash
# Continue previous session (recommended)
codex resume --last

# Or start fresh session
codex start

# List recent sessions
codex ls

# Resume specific session
codex resume <SESSION_ID>
```

---

## Troubleshooting Installation

### Issue: "codex: command not found"

**Solution 1: Reinstall**
```bash
# Uninstall
npm uninstall -g @openai/codex

# Reinstall
npm install -g @openai/codex

# Verify
which codex
codex --version
```

**Solution 2: Check PATH**
```bash
# macOS/Linux
echo $PATH

# Windows PowerShell
$env:Path -split ';'

# npm global location
npm config get prefix
```

### Issue: "OPENAI_API_KEY not set"

**Solution:**
```bash
# Verify API key is set
echo $OPENAI_API_KEY

# If empty, set it again
export OPENAI_API_KEY="your-key-here"

# Make permanent (macOS/Linux)
echo 'export OPENAI_API_KEY="your-key-here"' >> ~/.bashrc
source ~/.bashrc
```

### Issue: "Error: Invalid API key"

**Solution:**
1. Verify key at https://platform.openai.com/api-keys
2. Check for typos in key
3. Regenerate key if uncertain
4. Set environment variable again

### Issue: "Cannot find AGENTS.md"

**Solution:**
```bash
# Verify AGENTS.md exists in project
ls -la AGENTS.md

# Verify global AGENTS.md
ls -la ~/.codex/AGENTS.md

# Both should exist:
# ~/.codex/AGENTS.md (global)
# ./AGENTS.md (project)
```

### Issue: "Permission denied" (macOS/Linux)

**Solution:**
```bash
# Fix permissions
chmod +x ~/.codex

# Or reinstall with sudo (not recommended)
sudo npm install -g @openai/codex
```

---

## Verification Checklist

After installation, verify everything works:

```bash
# 1. API Key set
echo $OPENAI_API_KEY
# ✅ Should show your key

# 2. Codex CLI installed
codex --version
# ✅ Should show version (e.g., 1.2.3)

# 3. Config exists
cat ~/.codex/config.toml
# ✅ Should show configuration

# 4. Global AGENTS.md exists
cat ~/.codex/AGENTS.md | head -5
# ✅ Should show "Global Agent Instructions"

# 5. Connection works
cd ~/my-api
codex start
# ✅ Should start session
# Press Ctrl+C to exit
```

---

## Pricing & Costs

### Model Costs (as of 2026)

| Model | Input Cost | Use Case |
|-------|-----------|----------|
| **o4-mini** | $0.00005/1K | Fast, cheap tasks |
| **GPT-4o** | $0.003/1K | Balanced |
| **o3** | $0.02/1K | Complex reasoning |

### Cost Estimation
```
100K token session:
- o4-mini: ~$5
- GPT-4o: ~$300
- o3: ~$2,000

Typical daily usage:
- Light (1-2 sessions): $5-10/day (o4-mini)
- Medium (3-5 sessions): $15-50/day (mix)
- Heavy (10+ sessions): $100+/day (o3)
```

### Cost Optimization
```
1. Use o4-mini for simple tasks
2. Reserve o3 for complex decisions
3. Resume sessions (don't start fresh)
4. Monitor session token usage
5. Archive old sessions
```

---

## Next Steps

1. ✅ **Install Codex CLI** — Follow steps above
2. ✅ **Setup API Key** — Store securely
3. ✅ **Download This Repo** — Clone codex-howto
4. ✅ **Choose Template** — Pick your tech stack
5. ✅ **Customize AGENTS.md** — Add your project details
6. ✅ **Start Coding** — `codex start`

---

## Additional Resources

- **Codex Docs:** https://developers.openai.com/codex/
- **This Repository:** README.md → GETTING_STARTED.md
- **Best Practices:** guides/BEST_PRACTICES.md
- **Comparison:** guides/CODEX_vs_CLAUDE.md

---

## Getting Help

### Official Support
- OpenAI Help: https://help.openai.com
- Codex Docs: https://developers.openai.com/codex/

### Community
- GitHub Issues: In your codex-howto fork
- Stack Overflow: Tag `openai-codex`

### Debugging
```bash
# Enable debug output
export DEBUG=codex:*
codex start

# Check logs
ls -la ~/.codex/

# View session history
codex ls --verbose
```

---

**Installation complete!** Ready to code with Codex CLI. 🚀

→ Continue with [GETTING_STARTED.md](./GETTING_STARTED.md)
