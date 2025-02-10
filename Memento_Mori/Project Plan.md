
# Terminal Command Cheatsheet TUI

## Project Overview
A terminal-based user interface application that helps users organize and navigate through command-line references and cheatsheets. The application provides an intuitive way to categorize and access terminal commands through a namespace-based organization system.

## Technology Stack
- **Main Framework**: Go with [Bubble Tea](https://github.com/charmbracelet/bubbletea) (excellent TUI framework)
- **UI Components**: [Bubbles](https://github.com/charmbracelet/bubbles) (component library for Bubble Tea)
- **Styling**: [Lipgloss](https://github.com/charmbracelet/lipgloss) (style definitions)
- **YAML Handling**: `gopkg.in/yaml.v3` for configuration and notes
- **Testing**: Go's built-in testing framework

1. First, initialize your Go project:

```bash
mkdir cmdcheat
cd cmdcheat
go mod init cmdcheat
```

2. Install required dependencies:

```bash
go get github.com/charmbracelet/bubbletea
go get github.com/charmbracelet/bubbles
go get github.com/charmbracelet/lipgloss
go get gopkg.in/yaml.v3
```

Here's a suggested project structure:

```
cmdcheat/
├── cmd/
│   └── cmdcheat/
│       └── main.go
├── internal/
│   ├── ui/
│   │   ├── app.go        # Main application model
│   │   ├── namespace.go  # Namespace view
│   │   └── command.go    # Command view
│   ├── model/
│   │   ├── command.go    # Command data structures
│   │   └── namespace.go  # Namespace data structures
│   └── parser/
│       └── yaml.go       # YAML file parsing
├── configs/
│   └── style.go          # Lipgloss styles
└── data/                 # Command YAML files
    ├── git/
    │   └── basics.yaml
    └── docker/
        └── basics.yaml
```

## Interface Design
The interface consists of three main components:

### 1. Namespace Tab List (Left Panel)
- Displays a hierarchical list of namespaces (NS1, NS2, etc.)
- Each namespace can contain multiple elements (elem1, elem2)
- Selected namespace is highlighted
- Serves as the primary navigation structure
- Allows for nested categorization of commands

### 2. Command Display Area (Right Panel)
- Shows the contents of the selected namespace/element
- Larger viewing area for command details
- Organized into sections based on the selected element
- Supports scrollable content for longer command lists

### 3. Interactive Elements
- Highlighted selection indicator for active namespace/element
- Scrollable interface for both panels
- Clear visual hierarchy between namespaces and their elements

## User Experience
Users can:
- Navigate between different namespaces using keyboard controls
- View command references organized by categories
- Quickly access different sections of their command cheatsheet
- Add, edit, and organize commands in a structured manner
- Scroll through content when it exceeds the viewport

## File System Architecture 
- Each folders after the root are namespaces
- Cannot have multiple nested namedpaces

## Notes Syntax
Notes follows a specific syntax:
- Title displayed
- Command description
- Parameters that can be used
- Information about a parameter
- Multiple command can be stated into one file
- All files from a folder are all merged as one

## Note Syntax (YAML Format) Example
```yaml
title: "Git Basics"
commands:
  - name: "Git Init"
    description: "Initialize a new Git repository"
    syntax: "git init [directory]"
    parameters:
      - name: "directory"
        required: false
        description: "Optional directory to initialize"
    examples:
      - "git init"
      - "git init my-project"
    notes: "Creates a new .git directory"
```

## Technical Requirements
1. A text-based user interface framework for terminal applications
2. Support for keyboard navigation
3. Ability to handle hierarchical data structures
4. File system integration for storing and loading cheatsheet content
5. Support for markdown or similar formatting for command documentation

## Use Cases
- Quick reference for frequently used commands
- Organization of command-line tools by project or category
- Training material for new terminal users
- Personal knowledge base for terminal operations
