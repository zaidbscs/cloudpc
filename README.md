# Free Cloud Remote PC via GitHub Actions

Run a high-speed, free virtual Windows Remote PC directly inside GitHub Actions with unlimited bandwidth, custom credentials, and RDP tunneling powered by Ngrok.

## Features

* **100% Free**: Powered by GitHub Actions `windows-latest` runners.
* **High Performance**: Unlimited download and upload speeds using GitHub's enterprise infrastructure.
* **Full RDP Access**: Connect from any standard Microsoft Remote Desktop client.
* **Customizable**: Change your default username and password easily.

---

## Setup & Usage Guide

### 1. Fork or Clone this Repository

Clone this repository to your own GitHub account or use it as a template to get started.

### 2. Configure Ngrok Secret

To expose your RDP port securely, you need an Ngrok authtoken:

1. Create a free account on [Ngrok](https://ngrok.com/).
2. Copy your Ngrok Auth Token from your dashboard.
3. Go to your GitHub Repository -> **Settings** -> **Secrets and variables** -> **Actions**.
4. Add a new repository secret named `NGROK_AUTH_TOKEN` and paste your token.

### 3. Run the Workflow

1. Navigate to the **Actions** tab in your repository.
2. Select the **Remote Pc** workflow.
3. Click **Run workflow** to trigger the build.

### 4. Connect via Remote Desktop

1. Once the workflow reaches the **Create Tunnel** step, click into the running job logs.
2. Look for the active TCP tunnel address provided by Ngrok (e.g., `0.tcp.ngrok.io:XXXXX`).
3. Open your Remote Desktop Connection app on your local machine, paste the address, and log in using the credentials below.

---

## Default Credentials & Customization

The default user configured in the workflow is:

* **Username**: `runneradmin`
* **Password**: `P@ssw0rd!`

### How to Change Username and Password

Open your `.github/workflows/main.yml` file and modify line 19 to your desired username and password:

```yaml
- run: Set-LocalUser -Name "YourCustomUsername" -Password (ConvertTo-SecureString -AsPlainText "YourCustomPassword!" -Force)

```
