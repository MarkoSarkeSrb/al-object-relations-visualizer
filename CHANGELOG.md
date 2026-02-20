# Change Log

All notable changes to the "AL Object Relations Visualizer" extension will be documented in this file.

## [1.0.1] - 2025-02-20

### Added
- Support for namespace syntax in object references (e.g., `Namespace."Object Name"`)

## [1.0.0] - 2025-02-16

### Added
- Initial release
- Interactive relationship graph visualization using D3.js
- Workspace object scanning and analysis
- Click-to-open functionality for workspace objects
- **Detailed tooltips showing incoming and outgoing relations with context information**:
  - Field names for TableRelation references
  - Variable names for Record, Codeunit, and Enum declarations
  - SourceTable property for pages
  - Direct call vs variable usage distinction
- Support for multiple AL object types (Table, Page, Codeunit, Report, Query, Enum, Interface)
- Drag and drop node positioning
- Zoom controls
- Color-coded nodes by object type
- Context menu integration
- Relationship detection for:
  - Extends relationships
  - Implements interfaces
  - TableRelation references (with field names)
  - Record variables (with variable names)
  - Codeunit, Page, Report, and Enum references (with context)
  - SourceTable properties
- **Freeware license** - free for personal and commercial use

### Known Issues
- External object references from base app/system app shown as references only (cannot be opened)
- Initial scan may be slow for large projects