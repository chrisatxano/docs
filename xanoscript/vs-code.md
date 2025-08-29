---
noIndex: true
---

# VS Code Extension

### Overview

The XanoScript extension for Visual Studio Code provides comprehensive support for developing with XanoScript (`.xs` files), a domain-specific language designed for building backend applications with Xano. This extension offers syntax highlighting, code completion, error checking, and seamless integration with Xano workspaces.

### Features

#### Core Language Support

* **Syntax Highlighting**: Full syntax highlighting for XanoScript files (`.xs`)
* **Language Server**: Advanced language intelligence powered by a custom parser
* **Code Completion**: Intelligent autocomplete for functions, keywords, and syntax
* **Error Detection**: Real-time syntax and semantic error checking
* **Hover Documentation**: Detailed information on hover for functions and keywords

#### Xano Integration

* **Workspace Management**: Connect to and manage Xano workspaces directly from VS Code
* **Version Control**: Git-like workflow for managing changes, staging, and pushing to Xano
* **Real-time Sync**: Pull and push changes between local development and Xano workspace
* **Branch Management**: Switch between different branches and environments

### Installation

#### From VS Code Marketplace

1. Open Visual Studio Code
2. Press `Ctrl+Shift+X` (Windows/Linux) or `Cmd+Shift+X` (Mac) to open Extensions
3. Search for "XanoScript"
4. Click "Install"

#### Manual Installation

1. Download the `.vsix` file from the [GitHub repository](https://github.com/xano-labs/vscode-xs)
2. In VS Code, go to Extensions (`Ctrl+Shift+X`)
3. Click the "..." menu and select "Install from VSIX..."
4. Choose the downloaded `.vsix` file

### Configuration

#### Extension Settings

The extension provides several configuration options accessible via VS Code settings:

```json
{
  "xanoscript.xanoUrl": "https://app.xano.com",
  "xanoscript.draftMode": false
}
```

**Configuration Options**

* **`xanoscript.xanoUrl`** (string, default: `"https://app.xano.com"`)
  * The root URL for your Xano instance
* **`xanoscript.draftMode`** (boolean, default: `false`)
  * When `true`: API endpoints pull draft changes and pushed changes are saved as drafts
  * When `false`: API endpoints pull published changes only and pushed changes are immediately published

#### Language Configuration

The extension automatically configures:

* File associations for `.xs` files
* Bracket matching and auto-closing
* Surrounding pairs for selections
* Syntax highlighting rules

### Getting Started

#### Authentication

| <div><figure><img src="../.gitbook/assets/CleanShot 2025-08-29 at 15.34.33 (1).png" alt=""><figcaption></figcaption></figure></div> | <p></p><ol><li>Open the XanoScript view in the Activity Bar (left sidebar)</li><li>Click "Get Started" in the Files view</li><li>Click "Login to Xano" to authenticate with your Xano account (recommended)</li><li>Enter your Xano access token when prompted</li></ol> |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

{% hint style="info" %}
If you are unable to login with your Xano account, or prefer to not do so, you can manually provide a Metadata API Access Token ([#generate-an-access-token](../xano-features/metadata-api/#generate-an-access-token "mention"))  instead. Just choose "Enter Access Token" instead of "Login to Xano".
{% endhint %}

#### Workspace Setup

1. After login, select your instance from the dropdown, and then your workspace
2. Choose the appropriate branch if you are prompted
3. If you want to retain this configuration in the currently open project, click **Save Configuration** when prompted.
4. The extension will offer to pull the current state of your workspace to your local environment — this is recommended when setting up the extension in a new project.

#### 3. File Structure

The extension organizes your Xano workspace into a local file structure:

```
workspace/
├── functions/         # Custom functions
├── tables/            # Database tables
├── apis/              # API endpoints and groups
├── tasks/             # Scheduled tasks
└── workflow_tests/    # Test files
```

### Usage

#### Basic XanoScript Development

Press `Ctrl+Shift+X` (Windows/Linux) or `Cmd+Shift+X` (Mac) and type XanoScript to see the list of available commands.

Use commands such as **New Custom Function**, **New API Endpoint**, **New Table**, etc... to easily create new objects in your workspace with the proper naming convention. Using these commands will also give you the basic layout of that function stack in the newly created file.

Create a new `.xs` file and start coding:

```javascript
query auth/login verb=POST {
  description = "User authentication endpoint"
  
  input {
    email email? filters=trim|lower
    text password?
  }
  
  stack {
    db.get user {
      field_name = "email"
      field_value = $input.email
      output = ["id", "email", "password"]
    } as $user
    
    precondition ($user != null) {
      error_type = "accessdenied"
      error = "Invalid credentials"
    }
    
    security.check_password {
      text_password = $input.password
      hash_password = $user.password
    } as $pass_result
    
    precondition ($pass_result) {
      error_type = "accessdenied"
      error = "Invalid credentials"
    }
    
    security.create_auth_token {
      dbtable = "user"
      id = $user.id
      extras = {}
      expiration = 86400
    } as $authToken
  }
  
  response {
    value = {authToken: $authToken}
  }
}
```

#### Workspace Management

<figure><img src="../.gitbook/assets/CleanShot 2025-08-29 at 17.09.39.png" alt=""><figcaption></figcaption></figure>

**Viewing Changes**

* Use the "Changes" view to see modified files
* Files are categorized as "Changed" or "Staged"
* Click on files to view differences

**Staging Changes**

* Right-click on changed files and select "Stage current file"
* Use "Stage all changed files" to stage everything at once <sup>**(1)**</sup>
* Staged files appear in the "Staged" section

**Pushing Changes**

1. Stage the files you want to push
2. Click "Push Stage Changes to Xano" in the Changes view <sup>**(3)**</sup>
3. Changes will be uploaded to your Xano workspace

**Pulling Changes**

* Click "Pull latest changes from Xano" to sync with remote changes <sup>**(2)**</sup>
* Use "Reset this workspace to latest changes" to discard local changes

**Refresh Changes**

* If you are finding that your changes have not updated in real time, refresh your changes. <sup>**(4)**</sup>

### Extension Features

#### Syntax Highlighting

The extension provides comprehensive syntax highlighting for:

* **Keywords**: `query`, `function`, `task`, `stack`, `response`, `input`
* **Data Types**: `text`, `int`, `bool`, `decimal`, `timestamp`, `uuid`
* **Functions**: `db.get`, `security.check_password`, `debug.log`&#x20;
* **Variables**: `$input`, `$env`, `$auth`, `$var`
* **Operators**: `>=`, `<=`, `==`, `=`, `+`, `-`
* **Strings**: Single quotes, double quotes, and triple quotes
* **Comments**: Line and block comments

#### Code Completion

Intelligent autocomplete for:

* Function names and parameters
* Data types and keywords
* Variable references
* Built-in functions and methods

#### Error Detection

Real-time validation for:

* Syntax errors
* Semantic errors
* Missing required fields
* Invalid function calls

#### Hover Information

Hover over code elements to see:

* Function documentation
* Parameter descriptions
* Type information
* Usage examples

### Commands

#### Available Commands

Access commands via Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`):

**Authentication & Setup**

* `XanoScript: Login to Xano`
* `XanoScript: Select workspace`
* `XanoScript: Select branch`
* `XanoScript: Reinitialize XanoScript Config`

**File Management**

* `XanoScript: New Custom Function`
* `XanoScript: New Table`
* `XanoScript: New API Endpoint`
* `XanoScript: New API Group`
* `XanoScript: New Task`
* `XanoScript: New Workflow Test`

**Version Control**

* `XanoScript: Pull latest changes from Xano`
* `XanoScript: Push Stage Changes to Xano`
* `XanoScript: Stage current file`
* `XanoScript: Unstage current file`
* `XanoScript: Discard Changes`
* `XanoScript: View changes`
* `XanoScript: View conflicts`

**Utilities**

* `XanoScript: Upload Static Files`
* `XanoScript: Run Tests`
* `XanoScript: Refresh Changes`

### Views and Panels

#### XanoScript View

Located in the Activity Bar, provides access to:

**Changes View**

* Shows modified files in your workspace
* Displays staged and unstaged changes
* Provides push/pull controls
* Shows file differences

**Files View**

* Displays your Xano workspace structure
* Shows functions, tables, APIs, and tasks
* Allows creation of new resources
* Provides context menus for file operations

### Troubleshooting

#### Common Issues

**Authentication Problems**

* Ensure your access token is valid and not expired
* Check that you have the correct permissions for the workspace
* Verify the Xano URL in settings

**Sync Issues**

* Use "Pull latest changes" to resolve conflicts
* Check for network connectivity issues
* Verify workspace and branch selection

**Language Server Issues**

* Restart VS Code if syntax highlighting stops working
* Check the Output panel for language server errors
* Reinstall the extension if problems persist

#### Getting Help

* **Documentation**: [XanoScript Syntax Guide](https://docs.xano.com/xanoscript/vs-code)
