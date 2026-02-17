# AL Object Relations Visualizer

[![License: Freeware](https://img.shields.io/badge/License-Freeware-blue.svg)](LICENSE.md)
[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-support-yellow.svg)](https://www.buymeacoffee.com/YOUR_USERNAME)

Visualizes relationships between AL objects in Business Central projects using an interactive graph.

## Features

- **Interactive visualization** - Force-directed graph with D3.js
- **Automatic scanning** - Finds all AL objects in your workspace
- **Click to open** - Direct file opening by clicking on nodes (workspace objects only)
- **Detailed tooltips** - Shows incoming and outgoing relations for each object with contextual information:
  - Field names for TableRelation dependencies
  - Variable names for Record/Codeunit/Enum declarations
  - SourceTable properties for pages
  - Distinction between direct calls and variable usage
- **Color-coded nodes** - Different colors for different object types (table, page, codeunit, etc.)

## Usage

### Commands

- `AL Obj. Rel. Viz: Show Object Relations` - Shows all relationships in the workspace
- `AL Obj. Rel. Viz: Show Current File Relations` - Analyzes the currently open AL file

### Shortcuts

- Right-click in an AL file → "AL Obj. Rel. Viz: Show Current File Relations"

## Graph Controls

- **Drag & Drop** - Drag nodes to move them
- **Zoom** - Scroll with mouse wheel or use "Zoom In/Out" buttons
- **Hover** - Hover over nodes to see detailed information:
  - Object name, type, and ID
  - **Uses** (outgoing relations) - Objects that this object depends on
    - Shows WHERE the relation comes from (field name, variable name, etc.)
  - **Used by** (incoming relations) - Objects that depend on this object
    - Shows HOW they use it (through which field, variable, etc.)
  - Relation types (extends, uses, implements, etc.)
- **Click** - Click on green nodes to open files
- **Reset** - Return graph to initial view

### Context Information Types

The tooltip shows different types of context depending on how objects are related:

- **Field: [FieldName]** - TableRelation on a specific field
- **Variable: [VarName]** - Record, Codeunit, or Enum variable declaration
- **SourceTable** - Page's SourceTable property
- **Direct call** - Direct reference like `Codeunit::MyCodeunit`
- **Object extension** - Extends relationship
- **Interface implementation** - Implements relationship
- **Page/Report reference** - Direct Page or Report reference

### Example Tooltip

When you hover over a node, you'll see:
```
Sales Header
Type: table
ID: 36

Uses:
→ Customer (uses) via Field: Customer No.
→ Currency (uses) via Variable: CurrencyRec
→ Salesperson/Purchaser (uses) via Field: Salesperson Code

Used by:
← Sales Line (uses) via Field: Document No.
← Sales Invoice Header (extends) via Object extension
← Posted Sales Invoice (uses) via Variable: SalesHeader
```

## Object Types

- 🟢 Table
- 🔵 Page
- 🟠 Codeunit
- 🟣 Report
- 🔵 Query
- 🟡 Enum
- 🔴 Interface

## Requirements

- Visual Studio Code ^1.80.0
- AL Language extension

## Extension Settings

This extension contributes the following settings:

- `alDependencyVisualizer.maxDepth` - Maximum analysis depth (default: 3)
- `alDependencyVisualizer.includeSystemObjects` - Include system objects (default: false)
- `alDependencyVisualizer.colorScheme` - Color scheme for graph (default/dark/light/colorful)

## Known Issues

- Dependency objects (from base app, system app, etc.) are not available for opening - shown only as references
- Initial workspace scan may be slow for large projects

## Support the Project

If you find this extension helpful, consider supporting its development:

<a href="https://www.buymeacoffee.com/markosaricr" target="_blank">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" >
</a>

Your support helps maintain and improve this extension! ☕️

## License

This extension is licensed under a **Freeware License**. See [LICENSE.md](LICENSE.md) for details.

Free for personal and commercial use. ✨

## Release Notes

### 1.0.0

Initial release:
- Basic dependency graph
- Support for workspace objects
- Click-to-open functionality for workspace objects
- Visualization of dependencies to external objects (without ability to open)
