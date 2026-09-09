
To use Drive-Sync through Google Drive (alternative free approach of Obsidian Sync). **DriveSync requires you to create your own Google Cloud OAuth credentials**. We'll use:

```ASCII
Windows laptop → DriveSync → Google Drive → Android phone
```

---

# Part_1_Back_up_our_Obsidian_vault_first

**Do not skip this.**

Before touching synchronization:

1. Open our Obsidian vault folder in Windows Explorer.
    
2. Copy the **entire vault folder**.
    
3. Paste it somewhere safe, for example:
    

```text
Documents/
└── Obsidian Backup/
    └── MyVault/
```

Our vault should look something like:

```text
MyVault/
├── Notes/
├── Projects/
├── Attachments/
├── .obsidian/
└── ...
```

Keep this backup untouched until we're completely finished.

DriveSync itself specifically recommends backing up before the first synchronization because the initial reconciliation can modify local files

---

# Part_2_Install_DriveSync_on_our_laptop

Open Obsidian on our **Windows laptop**.

Go to:

```text
Settings
   ↓
Community plugins
   ↓
Browse
```

Search:

```text
DriveSync
```

We want the plugin called **DriveSync**.

Install → Enable

---

# Part_3_Create_a_Google_Cloud_project

We're basically telling Google:

> "I have an Obsidian plugin and I want to give it permission to access my Google Drive."

Go to:

[Google Cloud Console](https://console.cloud.google.com/?utm_source=chatgpt.com)

Sign in with the **same Google account we want to use for our Obsidian vault**.

Create a new project. For example:

```text
Project name:
Obsidian DriveSync
```

We don't need to make this project public.

---

# Part_4_Enable_Google_Drive_API

Inside our new Google Cloud project:

```text
APIs & Services
       ↓
Library
       ↓
Search "Google Drive API"
       ↓
Enable
```

That's it.

DriveSync needs the Google Drive API to communicate with our Drive

---

# Part_5_Configure_Google's_OAuth_consent_screen

Now go to:

```text
APIs & Services
       ↓
OAuth consent screen
```

Choose:

```text
External
```

unless you're using a Google Workspace organization.

Fill in the basic information.

For example:

```text
App name:
Obsidian DriveSync

User support email:
your Gmail

Developer contact:
your Gmail
```

Then add the Drive scope:

```text
https://www.googleapis.com/auth/drive
```

And **add your own Google account as a Test User**.

This part is important. Find:

```ASCII
Google Cloud Console
        ↓
Your project
        ↓
Google Auth Platform
        ↓
Audience
```

Look for:

```
Test users
```

Then click:

```
+ Add users
```

Add the **exact Gmail address you're currently using in the browser when DriveSync opens Google login**.

For example:

```
yourname@gmail.com
```

Then:

```
Save
```

Google's current documentation confirms that External apps in Testing mode require the account to be explicitly added under **Audience → Test users**.

We **do not need to publish the application**. Drive Sync's current instructions specifically recommend leaving it in Testing mode

---

# Part_6_Create_OAuth_credentials

Now:

```text
APIs & Services
       ↓
Credentials
       ↓
Create credentials
       ↓
OAuth client ID
```

For application type choose:

```text
Desktop app
```

Name it something like:

```text
Obsidian DriveSync
```

Google will give us:

```text
Client ID
Client Secret
```

**Keep those somewhere safe.**

DriveSync's current setup uses a Desktop OAuth client and normally uses redirect port `8520`.

---

# Part_7_Connect_DriveSync_to_Google

Back in Obsidian:

```text
Settings
   ↓
Community plugins
   ↓
DriveSync
```

We'll find fields for:

```text
Google OAuth Client ID
Google OAuth Client Secret
```

Paste the values we just got from Google.

Leave:

```text
Redirect port: 8520
```

unless we specifically configured another port.

Then open Obsidian's command palette:

```text
Ctrl + P
```

Search:

```text
DriveSync: Connect Google Drive
```

Run it.

Our browser should open.

Sign into our Google account and authorize DriveSync.

---

# Part_8_Let_the_first_sync_finish
Suppose our vault contains:

```text
MyVault/
├── Flutter/
│   ├── Riverpod.md
│   └── Architecture.md
├── Python/
│   └── FastAPI.md
├── Books/
├── Attachments/
└── .obsidian/
```

DriveSync will synchronize these with Google Drive.

It also synchronizes most `.obsidian` configuration, although some technical files such as workspace state are intentionally excluded.

**Don't start editing things on our phone yet.**

Wait until the laptop shows the sync is complete.

---

# Part_9_Install_Obsidian_on_our_Android_phone

On our phone, install:

**Obsidian**

Then open it and repeat the same process for installing DriveSync, setting up OAuth client id and secrets, and connect Google Drive
