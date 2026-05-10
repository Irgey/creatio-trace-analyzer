# Trace Analyzer

**Trace Analyzer** is a lightweight browser-based tool for analyzing Creatio trace logs collected via the `0/api/Tracing/v1/Index` endpoint.

The project works entirely in the browser, requires no backend, and can be used offline after downloading the repository.

Repository: https://github.com/Irgey/creatio-trace-analyzer

---

# Original Version

The original version focuses on tabular trace inspection and SQL diagnostics.

## Features

### Log Loading

Two input modes are supported:

#### File Upload
- Select a `.json` or `.txt` trace file
- The parser automatically processes line-by-line JSON objects

#### Paste Raw Trace Text
- Expand the input panel
- Paste trace content directly
- Press **Parse text**

---

### Interactive Table View

The parsed entries appear in a sortable, paginated table with columns:

- Duration
- Code
- StartedOn
- Id
- ParentId
- SQLText preview

Available operations:

- Sorting by any column
- Pagination for large logs
- Searching by selected column
- Resetting to original row order

---

### Detailed Drill-Down View

Each row includes a **Details** button.

The details section supports:

#### Event Properties
Displays all top-level event fields.

#### Formatted SQL
SQL queries are automatically formatted for readability.

#### SQL Parameters
Displays:
- Parameter name
- Type
- Value

#### Interpolated SQL
Builds SQL with substituted parameter values.

Supported parameter types:
- `11` — Integer
- `9` — GUID
- `16` — String
- `3` — Boolean
- `6` — DateTime

#### StackTrace
Formatted multi-line stack trace viewer.

---

### Built-in Statistics

The tool calculates:

- Total records
- Successfully parsed entries
- Parsing errors
- Results matching filters
- Maximum duration
- Average duration
- Code breakdown statistics

---

# Version 2 Features

The second version extends Trace Analyzer with advanced visualization, UI improvements, and execution-flow analysis.

## Execution Timeline

A SpeedScope-inspired execution timeline was added.

The timeline uses:
- `Id`
- `ParentId`
- `StartedOn`
- `Duration`
- `Code`

Capabilities:
- Visualize event duration on a time axis
- Display nested execution relationships
- Horizontal zoom support
- Time-range selection directly on the graph
- Selected event highlighting
- Parent/child relationship highlighting
- Automatic dimming of unrelated events
- Integrated Details panel for selected timeline events

For browser performance, timeline rendering is limited to 1000 events simultaneously.

---

## Event-Specific Details

The Details panel was improved:

### SQL Events
For `Code = SQL`:
- SQLText
- Parameters
- Interpolated SQL
- StackTrace

### Non-SQL Events
For other event types:
- SQL-specific sections are hidden
- `Data` object is displayed when available

Example:
```json
{
  "Code": "Contact:Changed",
  "Data": {
    "Id": "ee0af4a6-61b8-40ba-9ccd-aa4313120f09"
  }
}
```

---

## UI Improvements

### Themes
- Dark mode
- Light mode

### Visual Improvements
- Smooth hover animations
- Improved table layout
- Responsive timeline rendering
- Better stack trace wrapping
- Improved modal dialogs

### Help Popup
A built-in help dialog now provides:
- Tool description
- Repository link
- Quick usage information

---

## Usage

1. Open `index.html` in a modern browser
2. Upload a trace file or paste raw trace data
3. Use table filters and sorting
4. Open **Details** to inspect events
5. Open **Execution timeline**
6. Zoom and drag-select a time range for detailed analysis

---


## Notes

- All processing happens locally in the browser
- No data is sent to external services
- No backend is required
- Works with large trace files
- Timeline rendering is intentionally limited for browser responsiveness
