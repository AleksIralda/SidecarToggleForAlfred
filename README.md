# iPad Sidecar Connect for Alfred

A lightning-fast, frictionless Alfred Workflow to connect and disconnect macOS Sidecar devices. 

Built to bypass the unreliability of AppleScript UI-toggling (especially in macOS 15+ Sequoia), this workflow leverages the command line for instant, native-feeling device discovery and connection toggling.

## Features

* Dynamic Discovery: Automatically finds available Sidecar devices on your network.
* Smart Toggle: Press Enter to connect. Press Enter again to disconnect. Uses ioreg for millisecond-fast hardware state checks.
* Fail-safe Disconnect: Hold Cmd + Enter on any device to force a disconnect.
* Zero UI Scripting: Never worry about macOS updates breaking AppleScript osascript paths again.

## Prerequisites

* Alfred 5 (with Powerpack)
* macOS 13+ (Fully tested and optimized for macOS 15.7.1 Sequoia)
* SidecarLauncher (Compiled CLI binary by Ocasio-J)

## Installation

### 1. Install the CLI Tool (Required)

To run silently in the background, the SidecarLauncher executable must be placed in a standard system path. 

Open your Terminal and run the following commands:

​    curl -L -o SidecarLauncher https://github.com/Ocasio-J/SidecarLauncher/releases/latest/download/SidecarLauncher
​    sudo mkdir -p /usr/local/bin
​    sudo mv SidecarLauncher /usr/local/bin/
​    sudo chmod +x /usr/local/bin/SidecarLauncher

Note: You may be prompted to enter your macOS administrator password during the sudo steps.

### 2. Install the Alfred Workflow

1. Download the latest iPadSidecarConnect.alfredworkflow from the Releases tab.
2. Double-click the file to import it into Alfred.

## Usage

1. Open Alfred and type the keyword: sc (Change if Needed)
2. Select your iPad from the dynamically generated list.
3. Action Modifiers:
   * Enter: Toggles the connection.
   * Cmd + Enter: Force Disconnects the selected device.

## Under the Hood

This workflow separates concerns into a clean Frontend/Backend architecture:

* The UI (Script Filter): Executes /usr/local/bin/SidecarLauncher devices and parses the output.
* The Action (Run Script): Takes the payload and executes the connection toggle in the background.

## Credits

* CLI core logic provided by Ocasio-J's SidecarLauncher.
