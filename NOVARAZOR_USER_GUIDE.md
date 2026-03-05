# NovaRazor Extension - User Guide

**Version 4.0.0** | **VS Code Extension for Nova CMS Integration**

## Table of Contents
1. [Quick Start Guide](#quick-start-guide)
2. [Extension Overview](#extension-overview)
3. [Installation & Setup](#installation--setup)
4. [User Interface Guide](#user-interface-guide)
5. [Connection Management](#connection-management)
6. [Branch & Object Selection](#branch--object-selection)
7. [File Management & Status Tracking](#file-management--status-tracking)
8. [Update Operations & Modes](#update-operations--modes)
9. [Quick Pick Command Palette (Alt+N)](#quick-pick-command-palette-altn)
10. [Preview & Refresh](#preview--refresh)
11. [Logging System](#logging-system)
12. [VS Code Command Reference](#vs-code-command-reference)
13. [Cache Management & Performance](#cache-management--performance)
14. [Advanced Operations](#advanced-operations)
15. [Troubleshooting & Diagnostics](#troubleshooting--diagnostics)
16. [Tips & Best Practices](#tips--best-practices)
17. [Version Information](#version-information)

---

## Quick Start Guide

### Getting Started in 3 Steps

1. **Access the Extension**
   - Open VS Code Activity Bar (left side)
   - Click the NovaRazor icon ![NovaRazor Icon](media/nova.png)
   - The NovaRazor sidebar panel will open

2. **Connect to Nova**
   - Enter your Nova instance base URL
   - **Important**: Ensure you have CMS API credentials (not regular user login credentials)
   - Click "Send Base URL" to fetch branches
   - Select your target branch from the dropdown

3. **Work with Razor Objects**
   - Choose a Razor object from the updated dropdown
   - Use the interface to fetch, view, and update Razor code
   - Files are automatically managed and persisted

---

## Extension Overview

NovaRazor is a VS Code extension that integrates with Nova CMS API to provide Razor code management. The extension features a React-based UI, file management, status tracking, and change detection capabilities.

### Key Capabilities
- **Nova CMS Integration**: Direct API connectivity with your Nova instance
- **Quick Pick Command Palette**: Press `Alt+N` for instant access to all 16 operations
- **File Management**: Organized file creation with naming conventions
- **Status Tracking**: Visual feedback on file states and operations
- **Tab-sync & Persistence**: Sidebar auto-syncs with active file; tracking survives VS Code restarts
- **Multiple View Support**: Work with multiple Razor objects simultaneously
- **MD5-based Change Detection**: Upload optimization and version control
- **Preview Template**: Preview Razor templates with optional external link support
- **Refresh from Server**: Pull latest content from Nova without re-fetching the object
- **Multi-channel Logging**: Configurable log levels, channels, and export capabilities
- **API Version Selection**: Choose the target API version from the sidebar
- **Sync Operations**: Full sync, batch updates, and conflict resolution
- **Performance Diagnostics**: Built-in testing and monitoring tools

---

## Installation & Setup

### Requirements
- Visual Studio Code (latest version recommended)
- Nova CMS API access with valid **CMS API credentials** (not regular user credentials)
- Active network connection to your Nova instance

### Initial Configuration
1. Install the extension from the VS Code marketplace or load the `.vsix` file
2. Restart VS Code if prompted
3. The NovaRazor icon will appear in the Activity Bar
4. **Ensure you have CMS API credentials** - Regular user login credentials will not work
5. No additional VS Code settings configuration required

---

## User Interface Guide

### Sidebar Panel Components

The NovaRazor sidebar provides an interface for all extension operations:

![NovaRazor Sidebar Interface](media/nova.png)

**Main Interface Elements:**
- **Base URL Input**: Enter your Nova instance URL with connection status
- **API Version Selector**: Choose the target API version for your Nova instance
- **Connection Status Indicator**: Shows your Nova connection state
- **Branches Dropdown**: Select from available branches with search functionality
- **Razor Objects Dropdown**: Choose specific Razor objects with filtering
- **Action Buttons**: Buttons for fetch, update, preview, refresh, and management operations
- **File Status Overview**: Tracking of all managed files with persistent records
- **Update Mode Controls**: Configure single or batch update operations
- **External Links Checkbox**: Toggle loading of external resources in preview
- **Version Display**: Extension version information and settings

**Visual Workflow:**
```
[Enter Base URL] → [Connect] → [Select Branch] → [Select Razor Object] → [Perform Actions]
```

---

## Connection Management

### Nova Instance Connection

The connection management system provides connectivity to your Nova CMS instance with visual feedback.

#### Connection States

**Not Connected State:**
![Not Connected](media/Connection%20Settings%20-%20not%20connected..png)

When the extension is not connected to Nova, you'll see:
- Input field for base URL
- Connection status indicator
- Placeholder text
- Connect button

**Connecting State:**
![Connecting](media/Connection%20Settings%20-%20connecting..png)

During connection establishment:
- Loading indicator
- "Connecting..." status message
- Disabled controls to prevent conflicts

**Connected State:**
![Connected](media/Connection%20Settings%20-%20connected.png)

Once successfully connected:
- Green success indicator
- Connected status confirmation
- Enabled dropdown controls
- Ready for branch and object selection

#### Connection Setup Process

1. **Enter Base URL**
   - Input your Nova instance URL (e.g., `https://your-nova-instance.com`)
   - Ensure the URL is accessible and correct
   - **Important**: You must have CMS API credentials (not regular user login)

2. **Establish Connection**
   - Click "Send Base URL" to initiate connection
   - Extension validates URL and tests API accessibility
   - Connection status updates

3. **Verify Connection**
   - Green indicator confirms successful connection
   - Dropdown menus become available for selection
   - Error messages appear if connection fails

---

## Branch & Object Selection

### Branch Selection Interface

Once connected to Nova, the branch selection system provides search and filtering capabilities.

![Branch and Razor Object Selection](media/Branch%20and%20Razor%20Object%20Selection%20drop%20downs.png)

**Branch Dropdown Features:**
- List of available branches from your Nova instance
- Branch loading and display
- Visual hierarchy and organization

#### Branch Search

![Branch Search](media/Branch%20dropdown%20search.png)

The branch dropdown includes search functionality:
- **Instant Search**: Type to filter branches
- **Case-Insensitive**: Search works regardless of capitalization
- **Partial Matching**: Find branches with partial name matching
- **Keyboard Navigation**: Use arrow keys to navigate results
- **Quick Selection**: Click or press Enter to select

### Razor Object Selection

After selecting a branch, the Razor object dropdown becomes available.

![Razor Object Search](media/Razor%20object%20dropdown%20search.png)

**Razor Object Features:**
- Object listing for the selected branch
- Search and filtering capabilities
- Object metadata display (when available)
- Loading and responsive interface

#### Object Selection Process

1. **Select Branch First**
   - Choose your target branch from the dropdown
   - Extension loads objects for that branch
   - Loading indicators show progress

2. **Search Objects** (Optional)
   - Use the search functionality to find specific objects
   - Filter by name, identifier, or other metadata
   - Results update as you type

3. **Select Object**
   - Click on desired Razor object
   - Extension loads object details and prepares for operations
   - File creation process begins automatically

---

## File Management & Status Tracking

### Automatic File Creation

When you select a Razor object, the extension automatically creates a local file for editing.

![File Creation](media/Create%20new%20file%20for%20vs%20code%20after%20selecting%20a%20Razor%20object.png)

**File Creation Process:**
- Automatic file naming: `{branch}_{identifier}.cshtml`
- Content fetched from Nova and populated
- File opens in VS Code editor automatically
- Syntax highlighting and IntelliSense enabled
- File tracked for changes and sync status

### File Status Overview

The File Status Overview provides monitoring of all managed files in your workspace.

![File Status Overview](media/File%20status%20overview.png)

**Status Tracking Features:**
- **Status Updates**: Status changes when files are modified
- **Status Icons**: Visual indicators for file states
- **File Metadata**: Last modified, upload count, and sync information
- **Action Buttons**: Access to update and sync operations
- **Color-coded Status**: Green (synced), Yellow (modified), Red (errors)

#### Status Indicators Explained

| Icon | Status | Description |
|------|--------|-------------|
| ✅ | Synced | File is up-to-date with Nova |
| 📝 | Modified | File has local changes pending upload |
| ⏳ | Uploading | Upload operation in progress |
| ❌ | Error | Upload failed or sync error occurred |
| ❓ | Unknown | File status unknown or not tracked |

### Manual File Synchronization

For users who need manual control, synchronization options are available.

![Manual Sync](media/Resynch%20razor%20object%20file%20manually.png)

**Manual Sync Features:**
- Force synchronization of specific files
- Resolve sync conflicts manually  
- Override automatic change detection
- Confirmation dialogs
- Operation feedback

---

## Update Operations & Modes

### Single Update Mode

The default mode for updating individual Razor objects.

![Single Update Mode](media/Single%20update%20mode.png)

**Single Update Features:**
- Focus on one file at a time
- Visual feedback
- Loading animations
- Progress tracking with updates
- Success/error notifications

#### Single Update Process

1. **Make Changes**
   - Edit your Razor file in VS Code
   - Extension detects changes automatically
   - Status indicators update

2. **Upload Changes**
   - Click "Update" button in sidebar
   - Or use Command Palette: "NovaRazor: Update Razor Code"
   - Progress bar shows upload status

3. **Confirm Success**
   - Success notification appears
   - File status updates to "Synced"
   - Version history preserved in Nova

### Batch Update Mode

For updating multiple files simultaneously.

![Batch Update Mode](media/Update%20file%20to%20NovaDB%20modes.png)

**Batch Update Features:**
- Process multiple files simultaneously
- Individual progress tracking per file
- Progress overview
- Error handling per file
- Success reporting

#### Batch Update Process

1. **Prepare Multiple Files**
   - Edit multiple Razor files in your workspace
   - Each file tracked independently
   - Status indicators show which files have changes

2. **Initiate Batch Update**
   - Command Palette: "NovaRazor: Batch Update Razor Code"
   - Extension scans all tracked files for changes
   - Only modified files included in batch

3. **Monitor Progress**
   - Individual file progress bars
   - Overall batch progress indicator
   - Status updates
   - Error reporting per file

4. **Review Results**
   - Success/failure report
   - Per-file status updates
   - Logging output

---

## Cache Management & Performance

### Cache Status Monitoring

The extension includes cache management with monitoring capabilities.

![Cache Status](media/Cache%20status.png)

**Cache Status Features:**
- Cache size monitoring
- Performance metrics and statistics
- Memory usage tracking
- Hit/miss ratios for optimization
- Automatic cleanup status

#### Cache Metrics Explained

- **Cache Size**: Total amount of cached data
- **Cache Entries**: Number of cached items
- **Hit Ratio**: Percentage of successful cache retrievals
- **Memory Usage**: RAM consumption by cache
- **Last Cleanup**: Time of most recent cleanup

### Cache Configuration

Users can view cache configuration settings.

![Cache Configuration](media/Show%20cach%20configuration.png)

**Configuration Display:**
- Maximum cache size limits
- Cleanup thresholds and intervals
- Optimization settings
- Memory management parameters
- Maintenance schedules

### Log Level Management

For debugging and troubleshooting, the extension provides configurable logging levels.

![Log Level Settings](media/Set%20log%20level.png)

**Logging Features:**
- Multiple log levels (Error, Warning, Info, Debug)
- Log level switching
- Output channel integration
- Debug information for support

---

## Quick Pick Command Palette (Alt+N)

The NovaRazor Quick Pick Command Palette provides instant access to all extension operations from a single keyboard shortcut.

### How to Open

- Press **`Alt+N`** from anywhere in VS Code (any editor, any panel)
- Or use the standard VS Code command palette: `Ctrl+Shift+P` → "NovaRazor: Command Palette"

### Available Operations

The Quick Pick menu organizes 16 operations into 4 logical groups:

#### Primary Operations
| Operation | Description |
|-----------|-------------|
| Upload Razor Code | Upload current file to NovaDB |
| Batch Update | Upload all modified files |
| Refresh from Server | Pull latest content from server |
| Preview Template | Preview Razor template |
| Fetch Razor Objects | Load Razor objects for branch |
| Fetch Branches | Connect to NovaDB and load branches |

#### File & Sync
| Operation | Description |
|-----------|-------------|
| Re-sync Active File | Sync sidebar with current editor |
| Show File Status | Show file status panel |
| Sync Visual Indicators | Refresh all file indicators |

#### Logging
| Operation | Description |
|-----------|-------------|
| Set Log Level | Change logging verbosity |
| Toggle Log Channel | Enable/disable log channels |
| Clear Logs | Clear all log output |

#### Debug
| Operation | Description |
|-----------|-------------|
| Show Cache Status | View cache metrics |
| Show Change Cache | View file tracking data |
| List All Views | Show open Razor views |
| Reset Extension | Clear all data and reload |

### How It Works

- **Standalone commands** (File & Sync, Logging, Debug) execute directly
- **Sidebar-dependent commands** (Primary Operations) automatically focus the sidebar, wait for the webview to initialize, then trigger the action with your current state (base URL, selected branch, selected object)
- Type to filter operations by name or description
- Press `Escape` to dismiss without action

---

## Preview & Refresh

### Preview Template

Preview your Razor template directly within VS Code:

1. Select a Razor object and fetch its content
2. Click **"Preview Template"** in the sidebar or use `Alt+N` → "Preview Template"
3. A preview panel opens showing the rendered HTML output

**Preview Options:**
- **Allow Scripts**: Enable JavaScript execution in the preview (checkbox in sidebar)
- **Allow External Links**: Load external CSS/JS resources (checkbox in sidebar)

### Refresh from Server

Pull the latest content from Nova without re-fetching the entire object:

1. Have a Razor object open and selected
2. Click **"Refresh from Server"** in the sidebar or use `Alt+N` → "Refresh from Server"
3. The local file updates with the latest server content
4. Change detection recalculates automatically

This is useful when another team member has updated the same object on the server.

---

## Logging System

NovaRazor includes a multi-channel logging system for debugging and monitoring.

### Log Levels

| Level | Description |
|-------|-------------|
| **Error** | Critical failures only |
| **Warning** | Potential issues and deprecations |
| **Info** | General operational information |
| **Debug** | Detailed diagnostic output |

### Log Commands

- **Set Log Level**: Change the verbosity of log output (`Alt+N` → "Set Log Level")
- **Toggle Log Channel**: Enable or disable specific log channels (e.g., Cache Management, Core, File Operations)
- **Clear Logs**: Clear all log output from the output panel
- **Export Logs**: Copy log output for sharing or support

### Viewing Logs

1. Open VS Code Output panel (`Ctrl+Shift+U`)
2. Select "NovaRazor" from the dropdown
3. Logs appear in real-time during operations

---

## VS Code Command Reference

Access all commands via `Ctrl+Shift+P` (Windows/Linux) or `Cmd+Shift+P` (Mac), then type "NovaRazor":

### Core Operations
| Command | Description | Use Case |
|---------|-------------|----------|
| **NovaRazor: Command Palette** | Open Quick Pick menu (`Alt+N`) | Fast access to all operations |
| **NovaRazor: Add Razor Code** | Insert Razor code into current editor | Quick code insertion |
| **NovaRazor: Update Razor Code** | Update selected Razor object | Single object updates |
| **NovaRazor: Batch Update Razor Code** | Update multiple objects simultaneously | Bulk operations |
| **NovaRazor: Preview Template** | Preview Razor template in panel | Template verification |
| **NovaRazor: Refresh from Server** | Pull latest content from server | Server sync |

### Data Management
| Command | Description | Use Case |
|---------|-------------|----------|
| **NovaRazor: Fetch Dropdown Data** | Refresh branch and object lists | Data synchronization |
| **NovaRazor: Fetch Razor Objects** | Retrieve objects for current branch | Object list updates |
| **NovaRazor: Fetch Razor Object** | Get specific object details | Targeted retrieval |

### Sync & Visual Indicators
| Command | Description | Use Case |
|---------|-------------|----------|
| **NovaRazor: Sync Visual Indicators** | Update file status decorations | Status refresh |
| **NovaRazor: Full Sync Visual Indicators** | Complete indicator refresh | Comprehensive sync |
| **NovaRazor: Refresh File Decorations** | Reload file decoration states | Visual updates |
| **NovaRazor: Manual Sync with Active File** | Sync currently active file | Focused synchronization |

### Logging
| Command | Description | Use Case |
|---------|-------------|----------|
| **NovaRazor: Set Log Level** | Change logging verbosity | Debug configuration |
| **NovaRazor: Toggle Log Channel** | Enable/disable specific channels | Focused debugging |
| **NovaRazor: Clear Logs** | Clear all log output | Clean slate |

### Monitoring & Status
| Command | Description | Use Case |
|---------|-------------|----------|
| **NovaRazor: Show File Status Panel** | Display detailed file status | Status inspection |
| **NovaRazor: Show File Change Status** | View change detection results | Change analysis |
| **NovaRazor: Clear All Views** | Remove all open views | Workspace cleanup |
| **NovaRazor: List All Views** | Display all active views | View management |

### Cache Management
| Command | Description | Use Case |
|---------|-------------|----------|
| **NovaRazor: Show Change Cache** | View cached change data | Cache inspection |
| **NovaRazor: Clear Change Cache** | Reset change detection cache | Cache cleanup |
| **NovaRazor: Show Cache Status** | Display cache statistics | Performance monitoring |
| **NovaRazor: Show Cache Configuration** | View cache settings | Configuration review |
| **NovaRazor: Trigger Cache Cleanup** | Force cache maintenance | Manual cleanup |

### Testing & Diagnostics
| Command | Description | Use Case |
|---------|-------------|----------|
| **NovaRazor: Test Async MD5 Performance** | Run MD5 calculation benchmarks | Performance testing |
| **NovaRazor: Test Async MD5 Cancellation** | Test operation cancellation | Reliability testing |
| **NovaRazor: Stress Cache Test** | Execute cache stress testing | System validation |

---

## Advanced Operations

### MD5-based Change Detection

The extension uses sophisticated change detection with visual feedback:

**Automatic MD5 Calculation Features:**
- Files hashed on save and fetch operations
- Smart upload logic - only changed files uploaded
- Version history preservation with clean change tracking
- Performance optimization with async operations and cancellation support
- Real-time status updates during calculation

**Change Detection Process:**
1. **File Modification**: Extension detects when files are changed
2. **MD5 Calculation**: Background MD5 hash calculation begins
3. **Comparison**: New hash compared with Nova version
4. **Status Update**: Visual indicators updated
5. **Upload Optimization**: Only changed files marked for upload

### Multiple View Management

**Working with Multiple Objects:**
- Open different Razor objects simultaneously
- Each object creates its own file and view
- Files remain independent and manageable
- UI handles multiple active views
- Use "List All Views" command to see active objects
- Use "Clear All Views" for workspace reset

### Batch Operations with Progress Tracking

**Batch Update Workflow:**
1. **File Detection**: Extension scans workspace for modified Razor files
2. **Change Analysis**: MD5 comparison for each file
3. **Batch Preparation**: Only modified files included in batch
4. **Progress Monitoring**: Individual file progress with overall batch status
5. **Error Handling**: Per-file error reporting and recovery
6. **Success Confirmation**: Completion report with statistics

---

## Troubleshooting & Diagnostics

### Common Issues & Solutions

**Connection Problems:**

*Issue: Cannot connect to Nova instance*
- ✅ Verify Nova base URL is correct and accessible
- ✅ **Ensure you're using CMS API credentials, not regular user credentials**
- ✅ Check network connectivity and firewall settings
- ✅ Ensure Nova API endpoint is responding
- ✅ Use "Fetch Dropdown Data" to test connectivity
- ✅ Check VS Code Output panel for detailed error messages

*Issue: Connection drops frequently*
- ✅ Check network stability
- ✅ Verify Nova instance availability
- ✅ Review connection timeout settings
- ✅ Monitor cache status for performance issues

**File Sync Issues:**

*Issue: File status not updating*
- ✅ Use "Sync Visual Indicators" to refresh status
- ✅ Check "Show File Change Status" for detailed analysis
- ✅ Ensure files are saved in VS Code before sync
- ✅ Verify file permissions and workspace access
- ✅ Clear cache with "Clear Change Cache" if needed

*Issue: Upload operations failing*
- ✅ Check connection status indicator
- ✅ Verify file content is valid Razor code
- ✅ Review error messages in status indicators
- ✅ Try manual sync for individual files
- ✅ Check Nova instance disk space and permissions

**Performance Issues:**

*Issue: Slow MD5 calculations*
- ✅ Run "Test Async MD5 Performance" to benchmark speed
- ✅ Use "Show Cache Status" to monitor cache performance
- ✅ Close unused VS Code tabs to free memory
- ✅ Consider "Trigger Cache Cleanup" to optimize performance

*Issue: High memory usage*
- ✅ Use "Clear All Views" to reduce memory usage
- ✅ Monitor cache size with "Show Cache Status"
- ✅ Restart VS Code if memory usage remains high
- ✅ Run "Stress Cache Test" to identify bottlenecks

**Cache Problems:**

*Issue: Cache corruption or inconsistency*
- ✅ Use "Show Cache Configuration" to verify settings
- ✅ Use "Clear Change Cache" to reset cache state
- ✅ Run "Stress Cache Test" to validate cache stability
- ✅ Check disk space for cache storage
- ✅ Review cache cleanup logs for errors

### Diagnostic Commands

For technical support or advanced debugging:

1. **"Show File Status Panel"** 
   - Complete file state analysis
   - Detailed metadata for each tracked file
   - Change history and upload statistics
   - Error logs and diagnostic information

2. **"Show Cache Status"** 
   - Cache performance metrics and statistics
   - Memory usage and optimization data
   - Hit/miss ratios for performance tuning
   - Cleanup schedules and maintenance status

3. **"Test Async MD5 Performance"** 
   - Performance benchmarking for MD5 operations
   - Speed analysis and bottleneck identification
   - Cancellation testing for reliability
   - Resource usage monitoring

4. **"List All Views"** 
   - Active view inventory and management
   - Memory usage per view
   - File association mapping
   - Resource cleanup opportunities

### Advanced Debugging

**Output Panel Monitoring:**
- Open VS Code Output panel (`Ctrl+Shift+U`)
- Select "NovaRazor" from the dropdown
- Monitor real-time logs during operations
- Error messages include stack traces for debugging
- Performance metrics logged for analysis

**Log Channel Management:**
- Use `Alt+N` → "Toggle Log Channel" to enable/disable specific channels (e.g., Cache Management, Core, File Operations)
- Use `Alt+N` → "Set Log Level" to increase verbosity for detailed debugging
- Use `Alt+N` → "Clear Logs" for a fresh output before reproducing issues

**Performance Profiling:**
- Use diagnostic commands to identify bottlenecks
- Monitor resource usage during batch operations
- Compare performance metrics across different scenarios
- Document issues with timestamps for support

---

## Tips & Best Practices

### Workflow Optimization

**Efficient Daily Usage:**
1. **Start with Connection**: Connect to Nova instance once per session
2. **Use Alt+N**: Press `Alt+N` for instant access to any operation without navigating menus
3. **Keep Sidebar Visible**: Pin NovaRazor sidebar for quick access
4. **Use Professional Features**: Leverage search in dropdowns for efficiency
5. **Batch Operations**: Group related changes for bulk updates
6. **Monitor Status**: Keep File Status Overview visible for real-time feedback
7. **Let Automation Work**: Allow MD5 change detection to optimize uploads
8. **Preview Before Upload**: Use Preview Template to verify changes before pushing

**File Organization Best Practices:**
- Files automatically named with intelligent conventions
- Keep related files in organized VS Code workspace folders
- Use VS Code's built-in file search for quick navigation
- Leverage file status indicators for change management
- Close unused files to maintain performance

**Error Prevention Strategies:**
- Verify branch selection before fetching objects
- Save files in VS Code before running update operations
- Monitor connection status before major operations
- Use status indicators to confirm sync states
- Regular cache cleanup for performance

### Usage Patterns

**User Features:**
- **Multi-cursor Editing**: Combine with VS Code's multi-cursor for bulk changes
- **Find and Replace**: Use VS Code's find-and-replace across multiple Razor files
- **Git Integration**: Use VS Code's Git integration for version control
- **Task Automation**: Set up VS Code tasks for automated workflows
- **Extension Integration**: Combine with other VS Code extensions

**Workflows:**
- **Team Collaboration**: Use consistent branch and object naming
- **Code Reviews**: Use Git integration for peer review processes
- **Testing Integration**: Combine with testing frameworks for QA
- **Documentation**: Use Markdown preview for documentation alongside code
- **Performance Monitoring**: Use diagnostic commands

### Performance Optimization

**Memory Management:**
- Monitor active views and close unused ones
- Regular cache cleanup using diagnostic commands
- Restart VS Code periodically for long sessions
- Use batch operations efficiently to reduce overhead

**Network Efficiency:**
- Batch updates when possible to reduce API calls
- Let MD5 change detection prevent unnecessary uploads
- Use connection status monitoring to avoid failed operations
- Schedule major operations during optimal network conditions

**Resource Conservation:**
- Close unused browser tabs and applications
- Monitor system resources during large batch operations
- Use VS Code's built-in performance tools
- Regular maintenance of workspace files and folders

---

## Version Information

### Current Version: 4.0.0

**How to Check Your Version:**
- Version number displayed at bottom of NovaRazor sidebar
- Hover over version number for detailed build information
- Check VS Code Extensions panel for complete details and update status
- Use Command Palette for version-specific features

### Major Updates in v4.0.0

**New Features:**
- ✅ **Quick Pick Command Palette (Alt+N)**: Instant access to all 16 operations from a single shortcut, organized into 4 groups (Primary Operations, File & Sync, Logging, Debug)
- ✅ **Preview Template**: Preview Razor templates directly in VS Code with configurable script and external link permissions
- ✅ **Refresh from Server**: Pull latest content from Nova without re-fetching the entire object
- ✅ **API Version Selection**: Choose the target API version from the sidebar UI
- ✅ **External Links Checkbox**: Toggle loading of external CSS/JS resources in template preview
- ✅ **Multi-channel Logging System**: Set Log Level, Toggle Log Channel, Clear Logs, and Export Logs commands with dedicated output channels

**Reliability & Persistence:**
- ✅ **Tab-sync After Restart**: Sidebar automatically syncs with the active file when switching tabs, even after VS Code restarts
- ✅ **File Tracking Persistence**: Hash records always persisted to globalState immediately (not just at memory pressure thresholds), eliminating "No tracking record found" errors
- ✅ **Filename-based Recovery**: Lost tracking records are recovered from the filename pattern (`{branch}_{identifier}.cshtml`), preventing data loss
- ✅ **Partial Sync Support**: Sidebar syncs even when numeric object ID is unavailable, showing branch and file info

**Performance (Audit Fixes):**
- ✅ **Eliminated Redundant Re-renders**: Optimized React context to prevent full-tree re-renders
- ✅ **Debounced File Watchers**: Reduced overhead from rapid save events
- ✅ **LRU Cache with Bounded Size**: Configurable max entries, max age, and eviction policies
- ✅ **Async MD5 with Cancellation**: Non-blocking hash calculations with abort support

### Previous Versions

**v3.5.0:**
- Complete UI modernization with gradient card-based design
- SVG icon system (13+ custom icons replacing emoji)
- Eliminated artificial delays for immediate feedback
- Fixed cache race condition (phantom files after clearing)
- Fixed progress spinner timing issues
- Enhanced TypeScript type safety and React state management

**v3.3.0 and earlier:**
- MD5-based change detection system
- Cache management with monitoring
- Batch update capabilities
- Diagnostic and testing tools
- Eliminated race conditions in MD5 operations

---

## Support & Resources

### Getting Help

**Authentication Requirements:**
- **🔑 CMS API Credentials Required**: This extension requires CMS API credentials
- **❌ Regular User Passwords Won't Work**: Standard Nova login credentials are not supported
- **👤 Contact Administrator**: Reach out to your Nova administrator for CMS API access
- **🔐 Security**: API credentials provide access to Nova resources

**Debugging:**
1. **Check Connection Status**: Use indicators in sidebar
2. **Review Output Logs**: VS Code Output panel → NovaRazor channel
3. **Run Diagnostics**: Use Command Palette diagnostic commands
4. **Monitor Performance**: Cache status and performance checks
5. **Clear Cache**: Reset if experiencing issues

**Documentation Resources:**
- **User Guide**: This user guide
- **Implementation Docs**: Technical details in `docs/implementation/` folder
- **Change Log**: Version history in `CHANGELOG.md`
- **Troubleshooting**: Step-by-step diagnostic procedures
- **Best Practices**: Professional workflow recommendations

### Feature Requests & Feedback

The NovaRazor extension is actively maintained with regular updates and enhancements:

**Feedback Channels:**
- VS Code's built-in extension feedback system
- GitHub issues for bug reports and feature requests  
- Include diagnostic command outputs when reporting issues
- Provide Nova instance details (without credentials) for connectivity issues

**What to Include in Reports:**
- Extension version number (visible in sidebar)
- VS Code version and operating system
- Screenshots of error states or unexpected behavior
- Output from diagnostic commands
- Steps to reproduce the issue
- Expected vs. actual behavior

---

**You're now ready to use NovaRazor!**

This guide covers all aspects of the NovaRazor extension, from basic setup to advanced usage patterns. The extension is designed to provide an efficient workflow for Nova CMS integration.

**Quick Reference for New Users:**
1. 📥 Install extension and restart VS Code
2. 🔗 Connect to Nova instance with CMS API credentials
3. 🌿 Select branch and Razor object
4. ✏️ Edit files with change detection
5. 🚀 Upload changes with progress tracking
6. 📊 Monitor status with visual indicators

**For Advanced Users:**
- Press `Alt+N` for the Quick Pick Command Palette — fastest way to any operation
- Use batch operations for efficiency
- Preview templates before uploading with the Preview Template feature
- Use the multi-channel logging system to debug specific subsystems
- Use diagnostic commands for performance optimization
- Monitor cache and performance metrics

The extension continues to evolve with user feedback and Nova CMS developments. Stay updated through VS Code's extension update system for the latest features and improvements.
