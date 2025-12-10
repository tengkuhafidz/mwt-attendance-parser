# MWT Attendance Parser

A browser-based tool for analyzing student attendance data from CSV reports. Upload your attendance CSV and instantly see lateness statistics, filter by class, and identify students who need attention.

Built for [Madrasah Wak Tanjong](https://mwtanjong.edu.sg) by [10kb](https://10kb.co).

## Features

- **CSV Upload**: Drag-and-drop or browse to upload attendance reports
- **Lateness Classification**: Automatically categorizes arrivals as on-time, slightly late (7:35-7:40), moderately late (7:40-7:50), or very late (>7:50)
- **Student View**: See all students with their attendance records, sortable by name, class, or lateness count
- **Class Leaderboard**: Compare classes by punctuality, split into Primary and Secondary schools
- **Filtering**: Filter by class, search by student name, or click stat cards to show only on-time/late/critical students
- **Expandable Details**: Click any student row to see their specific late dates and times
- **Print Support**: Print-friendly styling for reports

## Usage

1. Open `index.html` in a browser
2. Upload a CSV file with the following format:
   - Column 1: Student ID
   - Column 2: Student Name
   - Column 3: Class (e.g., "P1A", "S2B")
   - Remaining columns: Dates with time values

### Accepted Time Values

| Value | Interpretation |
|-------|----------------|
| `7:30`, `07:45` | Arrival time |
| `Present` | On-time (no specific time) |
| `NA` or empty | Holiday/no school (if entire column is NA) |
| `Absent-Excused` | Excused absence |

## No Installation Required

This is a single HTML file with no dependencies to install. It uses PapaParse (loaded via CDN) for CSV parsing. All processing happens in your browser - no data is sent to any server.
