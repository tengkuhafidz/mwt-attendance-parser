# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MWT Attendance Parser is a single-file HTML application that parses CSV attendance reports and displays student lateness statistics. It runs entirely in the browser with no build system or server required.

## Running the Application

Open `index.html` directly in a browser. No build step or server needed.

## Architecture

**Single HTML File Structure:**
- All HTML, CSS, and JavaScript are contained in one file
- Uses PapaParse library (CDN) for CSV parsing
- No external dependencies to install

**Key Data Flow:**
1. User uploads CSV file via drag-drop or file picker
2. PapaParse parses CSV with headers
3. `processData()` transforms raw data into student records with attendance stats
4. Data is rendered in two views: Students list and Class leaderboard

**CSV Format Expected:**
- Column 1: Student ID
- Column 2: Student Name
- Column 3: Class
- Columns 4+: Date columns with time values (e.g., "7:35", "Present", "NA", "Absent-Excused")

**Time Classification Logic (in `classifyTime()`):**
- On-time: ≤7:35
- Slightly late: 7:35-7:40
- Moderately late: 7:40-7:50
- Very late: >7:50
- Columns where all students have "NA" are treated as holidays

**Global State:**
- `processedData`: Parsed student data and metadata
- `currentFilter`: Active stat card filter ('all', 'ontime', 'late', 'critical')
- `expandedRows`: Set of expanded student detail rows
