# My Azure Functions Notes 📝

## What I learned

**Azure Functions = code that runs in the cloud without servers**
- Only pay when it actually runs
- Perfect for APIs and webhooks
- No server management headaches

## Setup Steps (macOS)

1. **Install Core Tools**
   ```bash
   npm install -g azure-functions-core-tools@4 --unsafe-perm true
   ```

2. **Create Project in VS Code**
   - `Cmd+Shift+P` → "Azure Functions: Create New Project"
   - Choose Python, HTTP trigger, Function auth level

3. **Fix Python Version** (Azure Functions hates Python 3.13!)
   ```bash
   # Install Python 3.12 from python.org
   rm -rf .venv
   python3.12 -m venv .venv
   source .venv/bin/activate
   pip install azure-functions requests
   ```

4. **Set VS Code Interpreter**
   - `Cmd+Shift+P` → "Python: Select Interpreter"
   - Pick the `.venv/bin/python` one

5. **Test Locally**
   ```bash
   func start
   # Visit http://localhost:7071/api/your-function-name
   ```
![image](https://github.com/user-attachments/assets/036af9ef-390c-4796-ab65-68bead6fbec8)

## Key Files

- `function_app.py` - my actual code
- `requirements.txt` - what libraries I need
- `local.settings.json` - secrets (don't commit!)
- `.venv/` - isolated Python environment (don't commit!)

## Issues that I've had 

**"Import azure.functions could not be resolved"**
→ VS Code using wrong Python interpreter

**"func: command not found"**
→ Didn't install Azure Functions Core Tools

**"Python 3.7.x to 3.12.x is required"**
→ Python 3.13 too new, use 3.12

**"No connection" when testing**
→ Function didn't start properly, check terminal for errors

## Why These Choices?

- **HTTP Trigger**: Website sends data → function processes it
- **Function Auth**: Needs API key (secure but simple)
- **Virtual Environment**: Keeps project dependencies separate
- **Python**: Easy to work with APIs
