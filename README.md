# Trace Analyzer

**Trace Analyzer** — lightweight browser-based tool for analyzing Creatio trace logs that can be collected via 0/api/Tracing/v1/Index endpoint.  
It works entirely offline, requires no installation, and is optimized for large log files containing thousands of SQL and application events.

Trace Analyzer helps developers, support engineers, and performance analysts quickly inspect SQL queries, execution durations, parameters, and stack traces, enabling fast root-cause analysis.

---

## Features

### **1. Log Loading**
Two input modes are supported:

#### **File Upload**
- Select a `.json` or `.txt` trace file  
- The parser automatically processes line-by-line JSON objects

#### **Paste Raw Trace Text**
- Expand the input panel
- Paste trace content directly
- Press **Parse text**

Both modes produce a structured dataset ready for analysis.

---

## **2. Interactive Table View**
The parsed entries appear in a sortable, paginated table with columns:

- **Duration**
- **Code**
- **StartedOn**
- **Id**
- **ParentId**
- **SQLText** (short preview)

Available operations:

- Sorting by any column  
- Pagination for large logs  
- Searching by selected column  
- Resetting to original row order  

---

## **3. Detailed Drill-Down View**
Each row includes a **Details** button.  
Expanding it reveals:

### **Event Properties**
All top-level metadata of the trace entry.

### **Formatted SQL**
SQL queries are automatically formatted for readability:
- Keyword alignment  
- Normalized whitespace  
- Multi-line structure  

### **SQL Parameters**
A table showing:
- Parameter name  
- Type  
- Value  

### **Interpolated SQL**
A reconstructed SQL statement with real parameter values substituted into the query.

Supported parameter types:
- **11** — Integer  
- **9** — GUID  
- **16** — String  
- **3** — Boolean  
- **6** — DateTime  

Substitutions include inline comments:
/@ParamName/


A **Copy** button allows quick extraction of the fully interpolated query.

### **StackTrace**
A normalized multi-line stack trace, cleaned and formatted for readability.

---

## **4. Built-in Statistics**
Trace Analyzer automatically computes:

- Total records  
- Successfully parsed entries  
- Parsing errors  
- Results matching active filters  
- **Maximum Duration**  
- **Average Duration**  
- A frequency breakdown of `Code` values (sorted descending)

These metrics help identify slow or problematic operations quickly.

---

## **5. Language Support**
The interface supports:

- **English**  
- **Ukrainian**

Switching languages is available from the header at any time.

---

## Usage

1. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari)  
2. Upload a trace file or paste raw trace data  
3. Review the parsed results in the interactive table  
4. Use search, sorting, and pagination to narrow the dataset  
5. Open **Details** to inspect SQL, parameters, interpolated SQL, and stack trace  
6. Use built-in copy buttons to extract formatted statements

---
