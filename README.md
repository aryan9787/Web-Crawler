# Web Crawler Project Documentation

## Overview
This project implements a **basic web crawler** using Python that systematically browses web pages, extracts useful information, and stores it in a structured database.

The crawler starts from a given seed URL, explores linked pages within a defined domain, and collects relevant data such as page titles, text content, and link counts.

---

## Objectives
- Understand how web crawling works
- Extract meaningful data from web pages
- Store crawled data efficiently using a database
- Implement search functionality on collected data

---

## Technologies Used
- Python
- Requests – for HTTP requests  
- BeautifulSoup (bs4) – for HTML parsing  
- SQLite3 – for database storage  
- Logging – for tracking crawler activity  
- urllib – for URL handling  

---

## Project Workflow

### 1. Initialization
- Seed URL(s), allowed domain, and max pages defined
- Maintains visited and pending URL lists

---

### 2. Database Setup
SQLite database `crawler.db` with table `crawled_pages` storing:
- URL, title, content, links count, timestamp

---

### 3. Downloading Pages
Uses requests to fetch HTML content with timeout handling.

---

### 4. URL Validation
Filters URLs based on:
- Valid scheme (http/https)
- Allowed domain
- Skips files like PDFs, images, etc.

---

### 5. Extracting Links
- Parses HTML using BeautifulSoup
- Extracts anchor tags
- Converts relative URLs to absolute
- Adds valid links to queue

---

### 6. Extracting Content
- Removes unnecessary tags (script, style, etc.)
- Extracts title and clean text
- Limits text size

---

### 7. Data Storage
- Stores data in SQLite
- Uses INSERT OR IGNORE to prevent duplicates

---

### 8. Crawling Logic
For each page:
1. Download
2. Extract content
3. Save
4. Extract links
5. Queue new URLs

Stops when limit reached or queue empty.

---

### 9. Logging & Error Handling
- Logs crawling steps
- Handles errors gracefully

---

### 10. Data Retrieval
- Basic: URL and title
- Detailed: full page info with preview

---

### 11. Search Feature
Search pages using SQL LIKE query:
Finds pages containing specific keywords.

---

## Features
- Domain-restricted crawling
- Duplicate avoidance
- Structured storage
- Keyword search

---

## Limitations
- No JavaScript rendering
- No robots.txt handling
- Single-threaded

---

## Future Scope
- Multithreading
- NLP-based search
- Web UI
- Graph visualization

---

## Conclusion
This project demonstrates core concepts of web crawling, data extraction, and storage, forming a base for search engines.

