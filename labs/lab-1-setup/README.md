# Lab 1: Environment Setup

**Duration:** 45 minutes
**Objective:** Set up your development environment and obtain API credentials

---

## Overview

In this lab, you'll:
1. Create an IBM ID (if you don't have one)
2. Access your IBM TechZone VMs
3. Get workshop materials from Box
4. Join IBM Cloud and get watsonx Orchestrate credentials
5. Configure your environment
6. Test your connections

---

## Part 0: Prerequisites - IBM ID & TechZone Setup (10 min)

### Step 1: Create an IBM ID

If you don't already have an IBM ID, you'll need to create one using your work email address.

**Action Items:**

1. Navigate to the IBM ID creation page:
   **[https://myibm.ibm.com](https://myibm.ibm.com)** (right-click to open in a new tab)

2. Click **"Create an IBMid"**

3. Enter your information:
   - **Email address:** Use your work email
   - **Password:** Create a secure password
   - **First and Last Name**
   - **Country/Region**

4. Click **"Next"**

5. Check your email for a confirmation code from `ibmacct@iam.ibm.com`

6. Copy the **7-digit verification token** from the email

7. Paste the verification code and click **"Create Account"**

8. Accept the IBM Account Privacy notification by clicking **"Proceed"**

> ✅ **Success!** Your IBM ID is now active and ready to use.

---

### Step 2: Access IBM TechZone VMs

You will receive **two separate emails** from IBM TechZone for your workshop environments:

#### Email 1: IBM watsonx Orchestrate VM

You'll receive an email titled **"Join cloud account"** with an invitation to access the watsonx Orchestrate environment.

![Join Cloud Account Email](images/join%20cloud%20account.png)

**Action Items:**
1. Open the email from IBM TechZone
2. Click **"Join now"** or the invitation link
3. Accept the terms and conditions
4. You'll be redirected to IBM Cloud (continue to Part 2 below)

> 💡 **Note:** This email gives you access to the watsonx Orchestrate instance you'll use in the workshop.

---

#### Email 2: IBM Cloud VSI for IBM Bob IDE

You'll receive a second email titled **"Your environment is ready"** for the IBM Bob IDE virtual machine.

![Environment Ready Email](images/env%20ready%20email.png)

**Action Items:**

1. Open the **"Your environment is ready"** email from IBM TechZone

2. Click the link to go to your **TechZone Requests page**

![TechZone Requests Page](images/requests%20page.png)

3. On the requests page, scroll down to find your reservation:
   - Look for **"IBM Cloud VSI for IBM Bob IDE"**
   - Click to **expand** the reservation details

4. Find the **VDI (Virtual Desktop Interface) link** in the expanded section

![VDI Link](images/vdi%20link.png)

5. Click the VDI link to access the **Guacamole VM**

> 💡 **What is Guacamole?** It's a browser-based remote desktop that lets you access your development VM without installing any software.

---

### Step 3: Configure Guacamole Access

Once the Guacamole page loads, you'll need to enable clipboard access and connect to your desktop.

#### Enable Clipboard Access

**IMPORTANT:** Allow clipboard access so you can copy/paste between your local machine and the VM.

When the Guacamole page loads, look at the **top of your browser** for a clipboard permission prompt.

![Clipboard Access Prompt](images/clipboard%20access.png)

**Google Chrome:**
1. Look for the clipboard icon in the address bar (right side)
2. Click the icon
3. Select **"Allow"** for clipboard access
4. Alternatively: Click the lock icon → Site settings → Clipboard → Allow

**Microsoft Edge:**
1. Look for the clipboard icon in the address bar (right side)
2. Click the icon
3. Select **"Allow"** for clipboard access
4. Alternatively: Click the lock icon → Permissions for this site → Clipboard → Allow

**Mozilla Firefox:**
1. Look for the clipboard icon in the address bar (left side)
2. Click the icon
3. Select **"Allow"** for clipboard access
4. Alternatively: Click the shield icon → Permissions → Use the Clipboard → Allow

**Safari:**
1. Safari → Settings → Websites → Clipboard
2. Find the Guacamole site and set to **"Allow"**

> ⚠️ **Important:** Without clipboard access, you won't be able to copy/paste credentials and code between your computer and the VM!

---

#### Connect to Your Desktop

After enabling clipboard access:

![Guacamole Connections](images/connections.png)

1. On the Guacamole page, look for **"All Connections"** section

2. Expand **"IBM Cloud"** by clicking on it

3. Expand your environment name (it will match your reservation)

4. Click on **"VNC Desktop"** to launch the virtual desktop

5. Wait for the desktop to load (this may take 10-30 seconds)

**Expected Result:** You should now see a full Linux desktop environment in your browser with IBM Bob IDE ready to use.

> 💡 **Tip:** If the connection fails, refresh the page and try again. The VM may need a moment to fully start up.

**You now have access to:**
- ✅ IBM Cloud account with watsonx Orchestrate
- ✅ IBM Bob IDE virtual machine via Guacamole
- ✅ Clipboard access for easy copy/paste

> ⚠️ **Important:** Keep both emails handy - you'll need the credentials and links throughout the workshop!

---

### Step 4: Navigate the RHEL Desktop

You're now in a Red Hat Enterprise Linux (RHEL) desktop environment. Here are the basics:

#### Copy & Paste in the VM

**To copy text:**
- **Inside the VM:** `Ctrl+C` (standard)
- **From your computer to VM:** Copy on your computer (`Ctrl+C` or `Cmd+C`), then paste in VM with `Ctrl+Shift+V` or right-click → Paste

**To paste text:**
- **Inside the VM:** `Ctrl+V` (standard)
- **From VM to your computer:** Copy in VM (`Ctrl+C`), then paste on your computer (`Ctrl+V` or `Cmd+V`)

#### Basic Navigation

**Activities Menu:**
- Click **"Activities"** in the top-left corner to access applications
- Or press the **Super key** (Windows key / Command key)
- Search for applications by typing their name

![RHEL Activities Menu](images/rhel-activities.png)

**Common Applications:**
- **Firefox** - Web browser (pre-installed)
- **Terminal** - Command line interface
- **Files** - File manager

---

### Step 5: Authenticate IBM Bob IDE

Now you'll set up Bob IDE, your AI-powered development environment.

#### Open Bob IDE

1. Click **"Activities"** in the top-left corner

2. Type **"Bob"** in the search bar

3. Click on the **Bob IDE** application to launch it

#### Handle Initial Prompts

When Bob IDE first opens, you may see a keyring password prompt:

![Keyring Password Prompt](images/keyring.png)

**Action Items:**
1. Click **"Cancel"** on the keyring prompt
2. If it appears again, click **"Cancel"** a second time
3. This will dismiss the keyring dialog

Next, you'll see the Bob welcome screen:

![Bob Welcome Screen](images/bob-welcome-splash.png)

**Action Items:**
1. Click **"Skip for now"** to dismiss the welcome message
2. You'll now see the main Bob IDE interface

#### Authenticate with IBM ID

You should now see the Bob login panel on the right side:

![Bob Login Panel](images/bob-login.png)

**Action Items:**

1. In Bob's right-hand panel, click **"Sign in"** or **"Authenticate"**

2. Bob will open a link in **Firefox** (the default browser in the VM)

3. On the IBM login page, enter your **IBM ID email address** (your work email)

4. You'll be prompted to select an authentication method:

![Bob Authentication Methods](images/bob-authentication.png)

5. **Choose your authentication method:**

   **Option A: w3id Password (Recommended for VM)**
   - Select **"w3id password"**
   - Enter your IBM ID password
   - Click **"Sign in"**

   **Option B: IBM Verify Mobile App**
   - Select **"IBM Verify"**
   - Approve the authentication request on your mobile device
   - If you don't have IBM Verify set up, see the setup instructions below

   > ⚠️ **Important:** Do NOT select "Passkey" - it will not work inside the VM environment.

6. After successful authentication, Firefox will show a prompt: **"Open in Bob?"**

7. Click **"Open in Bob"** or **"Allow"**

8. You'll be redirected back to Bob IDE, now authenticated

**Expected Result:** Bob IDE is now authenticated and ready to use!

---

<details>
<summary><b>Setting Up IBM Verify (Optional)</b></summary>

If you want to use the IBM Verify mobile app for authentication:

1. Log in to **[www.ibm.com](https://www.ibm.com)** with your IBM ID credentials

2. Click on your **Profile** in the top-right corner

3. Navigate to **ID and password** → **TOTP** (Time-based One-Time Password)

4. Follow the on-screen instructions to set up TOTP

5. Download **IBM Verify** app on your smartphone or tablet:
   - **iOS:** [App Store](https://apps.apple.com/app/ibm-verify/id1162190392)
   - **Android:** [Google Play](https://play.google.com/store/apps/details?id=com.ibm.security.verifyapp)

6. Scan the QR code shown on the IBM website with the IBM Verify app

7. Your device is now registered for two-factor authentication

</details>

---

> 💡 **Tip:** If the browser doesn't open automatically, look for a URL in Bob's output panel and copy it to Firefox manually.

---

## Part 1: Get Workshop Materials (5 min)

### Step 1: Access Box Folder in the VM

Now that Bob is authenticated, you'll download the workshop materials.

#### Open Firefox and Access Box

1. In the VM, click **"Activities"** → type **"Firefox"** → open Firefox

2. Navigate to the workshop Box folder:
   ```
   https://ibm.box.com/v/navcanworkshop
   ```

3. Enter the **password** provided by your instructor

4. You'll see the workshop materials:
   - Workshop repository (ZIP file)
   - **kafka-credentials.md** (Markdown file) - Keep this tab open!
   - One-pager documentation (PDF)

#### Download and Extract Workshop Repository

1. **Download the workshop repository ZIP file** to your VM

2. Once downloaded, open the **Files** application (Activities → Files)

3. Navigate to **Downloads** folder

4. **Right-click** on the workshop ZIP file → **"Extract Here"**

5. You should now see an extracted workshop folder

#### Preview Kafka Credentials (Keep for Later)

**Important:** Keep the Box folder tab open in Firefox - you'll need to copy the Kafka credentials in Part 4.

1. In the Box folder, click on the **"kafka-credentials.md"** file

2. The markdown file will open in Box's web viewer showing:
   - `KAFKA_BOOTSTRAP_SERVERS`
   - `KAFKA_SASL_USERNAME`
   - `KAFKA_SASL_PASSWORD`

3. **Keep this tab open** - you'll copy these values directly into your `.env` file later

> 💡 **Tip:** Don't worry about copying the credentials now. We'll walk through exactly where to paste them in Part 4 when you configure your environment.

---

### Step 2: Open Workshop in Bob IDE

Now you'll open the workshop project in Bob IDE (similar to VS Code).

#### Open Folder in Bob

1. Switch back to **Bob IDE**

2. Click **"File"** in the top menu → **"Open Folder"**
   - Or use keyboard shortcut: `Ctrl+K` then `Ctrl+O`

3. Navigate to your **Downloads** folder

4. Select the **extracted workshop folder** (e.g., `bobathon-agentic-aviation-weather-warning-application-main`)

5. Click **"Open"** or **"Select Folder"**

#### Trust the Workspace

After opening the folder, Bob IDE will show a security prompt:

**"Do you trust the authors of the files in this folder?"**

```
IBM Bob provides features that may automatically execute files in this folder.

If you don't trust the authors of these files, we recommend to continue
in restricted mode as the files may be malicious.

~/Downloads/bobathon-agentic-aviation-weather-warning-application-main
```

**Action Items:**

1. Check the box that says **"Trust the authors of all files in the parent folder 'Downloads'"**

2. Click **"Yes, I trust the authors"**

> ✅ **Why this is safe:** You downloaded these files from the official workshop Box folder, so they are trusted workshop materials.

**Expected Result:** The workshop project is now open in Bob IDE with full functionality and the file explorer visible on the left side.

> 💡 **Tip:** You can also drag and drop the folder from Files into Bob IDE to open it.

#### Verify Workshop Files

In Bob's file explorer (left sidebar), you should see:
- `workshop/` - Your working directory
- `reference-implementation/` - Complete examples
- `labs/` - Lab instructions
- `requirements.txt` - Python dependencies
- `.env.example` - Configuration template
- `README.md` - Project documentation

> ✅ **Success!** You now have the workshop materials open in Bob IDE and are ready to start coding!

---

## Part 2: Join IBM Cloud & Get Orchestrate Credentials (10 min)

### Step 1: Accept IBM Cloud Invitation

You'll receive an email invitation to join an IBM Cloud account.

![IBM Cloud Invitation Email](images/cloud-invite.png)

**Action Items:**
1. Check your email for the IBM Cloud invitation
2. Click **"Join now"** in the email
3. Accept the terms and conditions
4. You'll be redirected to the IBM Cloud home page

### Step 2: Navigate to Resource List

Once logged into IBM Cloud:

![IBM Cloud Resource List](images/resource-list.png)

**Action Items:**
1. Click the **hamburger menu** (☰) in the top-left corner
2. Select **"Resource list"** from the sidebar
3. You'll see a list of available resources

### Step 3: Get watsonx Orchestrate Credentials

![watsonx Orchestrate API Details](images/orchestrate-api.png)

**Action Items:**
1. Find **"watsonx Orchestrate"** in your resource list
2. Click on the watsonx Orchestrate instance
3. Click **"Full details"** or **"View credentials"**
4. Copy and save:
   - **API URL** (e.g., `https://your-instance.watson-orchestrate.ibm.com`)
   - **API Key** (long string starting with letters and numbers)

> 💡 **Tip:** Keep these credentials in a safe place - you'll need them in the next step!

---

## Part 3: Set Up Python Environment in the VM (10 min)

### Step 1: Open Terminal in Bob IDE

In your Bob IDE window:

1. Click the **three dots (⋮)** in the top-left corner of Bob IDE
2. Select **"Terminal"** from the dropdown menu
3. Click **"New Terminal"**
   - Alternative: Use keyboard shortcut `Ctrl+Shift+` (backtick)

4. A terminal panel will open at the bottom of Bob IDE

**Expected Result:** You should see a bash terminal prompt in the RHEL VM.

### Step 2: Install Python 3.11

The RHEL VM comes with Python 3.9 by default, but we need Python 3.11 for the workshop.

#### Check Current Python Version

```bash
python3 --version
```

**Expected Output:** `Python 3.9.x`

#### Install Python 3.11

Run the following commands to install Python 3.11:

```bash
# Install Python 3.11 from RHEL repositories
sudo dnf install -y python3.11 python3.11-pip
```

> 💡 **Note:** You may be prompted for the sudo password. If so, ask your instructor for the VM password.

#### Verify Python 3.11 Installation

```bash
python3.11 --version
```

**Expected Output:** `Python 3.11.x`

> ✅ **Success!** Python 3.11 is now installed and ready to use.

### Step 3: Navigate to Workshop Directory

In the Bob IDE terminal, navigate to the workshop folder:

```bash
cd ~/Downloads/bobathon-agentic-aviation-weather-warning-application/workshop
```

> 💡 **Tip:** Adjust the path if you extracted the workshop to a different location.

### Step 4: Create Virtual Environment

Create an isolated Python environment for the workshop using Python 3.11:

```bash
python3.11 -m venv venv
```

> 💡 **What is a virtual environment?** It keeps your workshop dependencies separate from your system Python, preventing conflicts.

### Step 5: Activate Virtual Environment

In the RHEL VM terminal:

```bash
source venv/bin/activate
```

**Expected Result:** Your terminal prompt should now show `(venv)` at the beginning:
```
(venv) [user@hostname workshop]$
```

> ⚠️ **Important:** Keep this terminal open in Bob IDE and the virtual environment activated for all workshop labs!

---

<details>
<summary><b>Alternative: Running Locally (Optional - Not Recommended)</b></summary>

If you need to run the workshop on your local machine instead of the VM:

**macOS (using Homebrew):**
```bash
brew install python@3.11
python3.11 -m venv venv
source venv/bin/activate
```

**Windows:**
1. Download Python 3.11 from [python.org](https://www.python.org/downloads/)
2. Run the installer and check "Add Python to PATH"
3. Open Command Prompt or PowerShell:
```bash
python -m venv venv
venv\Scripts\activate  # Command Prompt
# OR
venv\Scripts\Activate.ps1  # PowerShell
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install python3.11 python3.11-venv
python3.11 -m venv venv
source venv/bin/activate
```

</details>

---

## Part 4: Configure Your Environment (5 min)

### Step 1: Create Environment File

In Bob IDE's terminal, check if `.env` already exists, then create it from the example:

```bash
# Check if .env already exists (to avoid overwriting your work)
ls -la .env

# If .env doesn't exist, create it from the example
cp .env.example .env
```

> ⚠️ **Important:** If you see `.env` already exists, **DO NOT run the `cp` command** - it will overwrite your credentials! Skip to Step 2 to edit your existing file.

**Expected Output:**
- If `.env` doesn't exist: `ls: cannot access '.env': No such file or directory` → Safe to run `cp` command
- If `.env` exists: Shows file details → **Skip the `cp` command** and go to Step 2

### Step 2: Open .env File in Bob IDE

1. In Bob IDE's file explorer (left sidebar), navigate to the `workshop` folder

2. Click on the `.env` file to open it in the editor

3. You'll see the template with placeholder values

### Step 3: Fill in Kafka Credentials from Box

Now you'll copy the Kafka credentials from the markdown file you kept open earlier.

**Action Items:**

1. Switch to **Firefox** and go back to the Box folder tab

2. Open the **"kafka-credentials.md"** file if not already open

3. In the markdown file viewer, you'll see three credential values

> ⚠️ **Important:** Copy each value **individually** (one at a time) to preserve formatting. Don't copy all three at once!

#### Copy Each Credential Individually:

**Step A: Copy KAFKA_BOOTSTRAP_SERVERS**
1. In Box markdown viewer: **Select only the bootstrap server value** (e.g., `pkc-xxxxx.us-east-1.aws.confluent.cloud:9092`)
   - Don't include the variable name, just the value
2. Copy it: `Ctrl+C`
3. Switch to Bob IDE
4. Find the line `KAFKA_BOOTSTRAP_SERVERS=your-cluster.confluent.cloud:9092`
5. Select and replace `your-cluster.confluent.cloud:9092` with your copied value
6. Paste: `Ctrl+V`
7. Verify the port number `:9092` is at the end

**Step B: Copy KAFKA_SASL_USERNAME**
1. Switch back to Firefox
2. In Box markdown viewer: **Select only the username/API key value**
   - Don't include the variable name, just the value
3. Copy it: `Ctrl+C`
4. Switch to Bob IDE
5. Find the line `KAFKA_SASL_USERNAME=your-api-key`
6. Select and replace `your-api-key` with your copied value
7. Paste: `Ctrl+V`

**Step C: Copy KAFKA_SASL_PASSWORD**
1. Switch back to Firefox
2. In Box markdown viewer: **Select only the password/API secret value**
   - Don't include the variable name, just the value
3. Copy it: `Ctrl+C`
4. Switch to Bob IDE
5. Find the line `KAFKA_SASL_PASSWORD=your-api-secret`
6. Select and replace `your-api-secret` with your copied value
7. Paste: `Ctrl+V`

> 💡 **Tip:** Make sure there are no extra spaces before or after the values! Each value should be on its own line in the .env file.

### Step 4: Fill in watsonx Orchestrate Credentials

Now add your watsonx Orchestrate credentials from IBM Cloud (Part 2).

**Action Items:**

1. Find the line `ORCHESTRATE_API_URL=https://your-instance.watson-orchestrate.ibm.com`

2. Replace with your watsonx Orchestrate API URL from IBM Cloud

3. Find the line `ORCHESTRATE_API_KEY=your-orchestrate-api-key`

4. Replace with your watsonx Orchestrate API Key from IBM Cloud

### Step 5: Save the .env File

1. In Bob IDE, press `Ctrl+S` to save the `.env` file

2. Verify all credentials are filled in (no placeholder text remaining)

**Your .env file should now look like this (with your actual values):**

```bash
# Confluent Kafka Configuration
KAFKA_BOOTSTRAP_SERVERS=pkc-xxxxx.us-east-1.aws.confluent.cloud:9092
KAFKA_SASL_USERNAME=ABCDEFGHIJKLMNOP
KAFKA_SASL_PASSWORD=long-secret-string-here

# Kafka Topics (already configured - don't change)
WEATHER_TOPIC=weather_events
FLIGHT_TOPIC=flight_telemetry

# watsonx Orchestrate Configuration
ORCHESTRATE_API_URL=https://us-south.ml.cloud.ibm.com/ml/v1/...
ORCHESTRATE_API_KEY=abc123xyz...

# API Configuration (leave as-is)
API_HOST=0.0.0.0
API_PORT=8000
```

**Credential Reference Table:**

| Variable | Source | Example Format |
|----------|--------|----------------|
| `KAFKA_BOOTSTRAP_SERVERS` | Box - kafka-credentials.md | `pkc-xxxxx.region.aws.confluent.cloud:9092` |
| `KAFKA_SASL_USERNAME` | Box - kafka-credentials.md | `ABCDEFGHIJKLMNOP` |
| `KAFKA_SASL_PASSWORD` | Box - kafka-credentials.md | `long-secret-string` |
| `ORCHESTRATE_API_URL` | IBM Cloud - watsonx Orchestrate | `https://us-south.ml.cloud.ibm.com/...` |
| `ORCHESTRATE_API_KEY` | IBM Cloud - watsonx Orchestrate | `abc123xyz...` |

### Step 2: Install Python Dependencies

Make sure your virtual environment is activated (you should see `(venv)` in your prompt), then install all required packages:

```bash
pip install -r requirements.txt
```

> ⏱️ **Note:** This may take 2-3 minutes to complete.

**What's being installed:**
- **IBM watsonx Orchestrate ADK** - For building AI agents
- **Kafka clients** - For streaming data
- **Flask & Flask-CORS** - For the API server (Lab 4)
- **FastAPI** - Alternative web framework
- **Other utilities** - python-dotenv, requests, etc.

**Expected Output:**
```
Successfully installed ibm-watsonx-orchestrate-2.8.0 confluent-kafka-2.3.0 flask-3.0.0 ...
```

---

## Part 5: Test Your Connections (5 min)

### Test Kafka Connection

Run the Kafka connection test:

```bash
python backend/kafka_utils.py
```

**Expected Output:**
```
✅ Kafka connection successful!
```

**If you see an error:**
- Double-check your Kafka credentials in `.env`
- Ensure `KAFKA_BOOTSTRAP_SERVERS` includes the port (`:9092`)
- Verify there are no extra spaces in your credentials

### Test Python Environment

Verify Python packages are installed:

```bash
python -c "import kafka; import fastapi; print('✅ All packages installed!')"
```

**Expected Output:**
```
✅ All packages installed!
```

---

## Troubleshooting

### Issue: Can't access Guacamole VM

**Solution:**
- Verify you clicked the correct VDI link from TechZone
- Refresh the browser page
- Check that your TechZone reservation is active
- Contact your instructor if the VM isn't accessible

### Issue: Clipboard not working in VM

**Solution:**
- Ensure you allowed clipboard access in your browser (see Step 3)
- Try refreshing the Guacamole page
- Use `Ctrl+Shift+V` to paste into the VM terminal
- Check browser permissions: Settings → Site Settings → Clipboard

### Issue: Bob IDE won't authenticate

**Solution:**
- Make sure Firefox opened the authentication page
- If no browser opened, look for the URL in Bob's output panel
- Copy the URL and paste it into Firefox manually
- Clear Firefox cookies and try again: Settings → Privacy & Security → Clear Data

### Issue: Wrong Python version in VM

**Solution:**
```bash
# In Bob IDE terminal
# Deactivate current environment
deactivate

# Remove old venv
rm -rf venv

# Create new venv with Python 3
python3 -m venv venv

# Activate and reinstall
source venv/bin/activate
pip install -r requirements.txt
```

### Issue: "Module not found" error

**Solution:**
```bash
# In Bob IDE terminal
# Make sure venv is activated (you should see (venv) in prompt)
source venv/bin/activate

# Reinstall packages
pip install -r requirements.txt --upgrade
```

### Issue: Can't find workshop folder

**Solution:**
- Check your Downloads folder: `cd ~/Downloads`
- List files: `ls -la`
- If ZIP wasn't extracted: `unzip bobathon-*.zip`
- Navigate to extracted folder: `cd bobathon-agentic-aviation-weather-warning-application/workshop`

### Issue: Kafka connection fails

**Checklist:**
- [ ] Credentials copied correctly from Box folder (no extra spaces)
- [ ] Bootstrap server includes port number (`:9092`)
- [ ] Using the correct credentials from the Kafka credentials file
- [ ] VM has internet connectivity (test with `ping google.com`)
- [ ] `.env` file is in the correct directory

### Issue: Can't find watsonx Orchestrate in IBM Cloud

**Solution:**
- Open Firefox in the VM and go to IBM Cloud
- Refresh the resource list page
- Check that you accepted the IBM Cloud invitation email
- Contact your instructor if the resource isn't visible

---

<details>
<summary><b>Local Machine Troubleshooting (If Not Using VM)</b></summary>

### Issue: Virtual environment not activating on Windows PowerShell

**Solution:**
```powershell
# Enable script execution
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Then activate
venv\Scripts\Activate.ps1
```

### Issue: Python not found on macOS

**Solution:**
```bash
# Install Python 3.11 via Homebrew
brew install python@3.11

# Create venv
python3.11 -m venv venv
source venv/bin/activate
```

</details>

---

## Verification Checklist

Before moving to Lab 2, ensure you have:

- [ ] Created an IBM ID (or logged in with existing ID)
- [ ] Received and accessed both TechZone VM emails
- [ ] Accessed IBM Cloud via watsonx Orchestrate invitation
- [ ] Accessed IBM Bob IDE via Guacamole VDI link
- [ ] Downloaded workshop materials from Box
- [ ] Joined IBM Cloud account
- [ ] Obtained watsonx Orchestrate credentials
- [ ] Installed Python 3.11
- [ ] Created and activated virtual environment (see `(venv)` in prompt)
- [ ] Created and configured `.env` file
- [ ] Installed Python dependencies
- [ ] Successfully tested Kafka connection
- [ ] Verified Python packages are installed

> 💡 **Remember:** Always activate your virtual environment (`source venv/bin/activate`) before running workshop commands!

---

## Next Steps

✅ **Congratulations!** Your environment is set up and ready.

Proceed to **Lab 2: Kafka Consumer** to start building your aviation warning system!

---

## Quick Reference

**Important Files:**
- `.env` - Your configuration file (keep this private!)
- `requirements.txt` - Python dependencies
- `backend/kafka_utils.py` - Kafka helper functions

**Need Help?**
- Check the troubleshooting section above
- Ask your instructor
- Review the example files in `examples/`

---

**Lab 1 Complete!** 🎉