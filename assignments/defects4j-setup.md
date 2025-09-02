# Defects4J Setup Instructions

## Prerequisites

Before setting up Defects4J, ensure you have the following installed:

### Required Software
- **Java 11** (JDK 11) - **Important**: Latest Defects4J requires Java 11 for proper bug reproduction
- **Git** - For cloning repositories
- **Perl** - Required for Defects4J scripts
- **Python 3** - For some analysis tools
- **Maven** and **Gradle** - For building projects

### Platform-Specific Prerequisites

#### macOS
```bash
# Install Homebrew if not already installed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install required tools
brew install git perl python3 maven gradle

# Install Java 11 (OpenJDK)
brew install --cask temurin11
```

#### Ubuntu/Debian Linux
```bash
# Update package list
sudo apt update

# Install required tools
sudo apt install git perl python3 maven gradle curl

# Install Java 11
sudo apt install openjdk-11-jdk

# Set JAVA_HOME (add to ~/.bashrc or ~/.zshrc)
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
```

#### Windows (using WSL2 recommended)
```bash
# Install WSL2 and Ubuntu, then follow Ubuntu instructions above
# Alternatively, install tools manually:
# - Git for Windows
# - Strawberry Perl
# - OpenJDK 11
# - Maven and Gradle
```

## Step 1: Clone Defects4J Repository

```bash
# Clone the official Defects4J repository
git clone https://github.com/rjust/defects4j.git

# Navigate to the cloned directory
cd defects4j
```

## Step 2: Initialize Defects4J

```bash
# Run the initialization script
./init.sh

# Set timezone (REQUIRED for proper test execution)
export TZ=America/Los_Angeles

# Add Defects4J to your PATH (add this to your ~/.bashrc or ~/.zshrc)
export PATH="$PWD/framework/bin:$PATH"
```

**For permanent setup, add to your shell profile**:
```bash
# For bash users (add to ~/.bashrc)
echo 'export PATH="/path/to/defects4j/framework/bin:$PATH"' >> ~/.bashrc
echo 'export TZ=America/Los_Angeles' >> ~/.bashrc
source ~/.bashrc

# For zsh users (add to ~/.zshrc) 
echo 'export PATH="/path/to/defects4j/framework/bin:$PATH"' >> ~/.zshrc
echo 'export TZ=America/Los_Angeles' >> ~/.zshrc
source ~/.zshrc
```

## Step 3: Verify Installation

```bash
# Check that defects4j command is available
defects4j

# You should see output showing available commands
# If you get "command not found", check your PATH setting
```

## Step 4: Test Basic Functionality

```bash
# List available projects
defects4j pids

# Get information about a specific project
defects4j info -p Lang

# Test checkout functionality with a simple example
mkdir test-workspace
cd test-workspace

# Checkout a bug (this may take a few minutes for first checkout)
defects4j checkout -p Lang -v 1b -w Lang-1

# Navigate to the checked out project
cd Lang-1

# Compile the project
defects4j compile

# Run the failing test
defects4j test
```

If all steps complete successfully, your Defects4J installation is ready!

## Common Issues and Solutions

### Issue 1: Java Version Problems
**Problem**: "Unsupported Java version" or compilation errors
**Solution**:
```bash
# Check Java version
java -version

# Should show version 11.x.x
# If not, set JAVA_HOME correctly:
export JAVA_HOME=/path/to/java11
export PATH="$JAVA_HOME/bin:$PATH"
```

### Issue 2: Permission Denied
**Problem**: Permission denied when running init.sh
**Solution**:
```bash
chmod +x init.sh
chmod +x framework/bin/defects4j
```

### Issue 3: Missing Dependencies
**Problem**: "Command not found" for perl, python3, maven, etc.
**Solution**: Install missing dependencies using your package manager

### Issue 4: Network Issues During Checkout
**Problem**: Slow downloads or timeouts
**Solution**:
```bash
# Increase timeout settings
export D4J_TIMEOUT=300

# Or use alternative mirror if available
# Check defects4j documentation for mirror options
```

### Issue 5: Disk Space
**Problem**: Not enough disk space
**Solution**: Each checked-out project can be 100MB-1GB. Ensure you have at least 10GB free space for multiple projects.

## Workspace Organization

Create a organized workspace structure:

```bash
# Create main workspace directory
mkdir ~/defects4j-workspace
cd ~/defects4j-workspace

# Create subdirectories for different assignments
mkdir assignment1
mkdir assignment2
# etc.

# For assignment 1, create group-specific directories
cd assignment1
mkdir group1-bugs
mkdir group2-bugs
# etc.
```

## Quick Reference Commands

### Essential Defects4J Commands

```bash
# List all available projects
defects4j pids

# Get project information
defects4j info -p <PROJECT>

# List all bugs for a project
defects4j bids -p <PROJECT>

# Checkout buggy version
defects4j checkout -p <PROJECT> -v <BUG_ID>b -w <WORK_DIR>

# Checkout fixed version  
defects4j checkout -p <PROJECT> -v <BUG_ID>f -w <WORK_DIR>

# Compile project
defects4j compile

# Run all tests
defects4j test

# Run specific test
defects4j test -t <TEST_CLASS>::<TEST_METHOD>

# Get coverage information
defects4j coverage

# Export properties (build files, test directories, etc.)
defects4j export -p dir.bin.classes
defects4j export -p dir.bin.tests
```

### Project Name Reference
- **Lang** = Commons-Lang
- **Math** = Commons-Math  
- **Chart** = JFreeChart
- **Time** = Joda-Time
- **Closure** = Closure Compiler
- **Mockito** = Mockito
- **Cli** = Commons-CLI
- **Codec** = Commons-Codec
- **Collections** = Commons-Collections
- **Compress** = Commons-Compress
- **Csv** = Commons-CSV
- **Gson** = Gson
- **JacksonCore** = Jackson Core
- **JacksonDatabind** = Jackson Databind
- **JacksonXml** = Jackson XML
- **Jsoup** = jsoup
- **JxPath** = Commons-JXPath

## Getting Help

### Documentation
- **Official Documentation**: https://github.com/rjust/defects4j
- **Research Papers**: https://people.cs.umass.edu/~rjust/defects4j/
- **Bug Database**: Browse available bugs and their descriptions

### Troubleshooting
- **Check Issues**: https://github.com/rjust/defects4j/issues
- **Course Forum**: Post questions on Piazza
- **Office Hours**: Attend TA or instructor office hours

### Testing Your Setup
Before starting the assignment, verify your setup works with this simple test:

```bash
# Create test directory
mkdir ~/defects4j-test
cd ~/defects4j-test

# Checkout a simple bug
defects4j checkout -p Lang -v 1b -w test-lang1
cd test-lang1

# This should succeed without errors
defects4j compile
defects4j test

# Check that exactly one test fails
echo "Setup successful if exactly 1 test fails!"
```

If you encounter any issues during setup, document the error messages and seek help early - don't wait until the assignment deadline!