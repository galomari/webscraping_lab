
# Boldest - Web Scraping Lab

Welcome to the Boldest Web Scraping Lab. This lab is designed to teach you the basics of web scraping using Python, BeautifulSoup, requests, and pandas. By the end of this lab, you will be able to scrape data from HTML pages and process it into a usable format.

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Objectives](#objectives)
- [Beautiful Soup Object](#beautiful-soup-object)
- [Tags and Navigable Strings](#tags-and-navigable-strings)
- [Children, Parents, and Siblings](#children-parents-and-siblings)
- [HTML Attributes](#html-attributes)
- [Finding Elements](#finding-elements)
- [Scraping Web Content](#scraping-web-content)
- [Scraping Data into DataFrames](#scraping-data-into-dataframes)

## Introduction

Beautiful Soup is a Python library used for web scraping purposes to pull data out of HTML and XML files. This lab will guide you through using BeautifulSoup and related libraries to extract and process web data.

## Installation

To install the required libraries, execute the following commands:

```bash
!mamba install bs4==4.10.0 -y
!pip install lxml==4.6.4
!mamba install html5lib==1.1 -y
!pip install requests==2.26.0
Objectives
After completing this lab, you will be able to:

Parse HTML documents using BeautifulSoup.
Navigate HTML documents and extract data.
Use BeautifulSoup to find specific elements by tag, class, id, and more.
Scrape web content and convert it into pandas DataFrames for analysis.
Beautiful Soup Object
BeautifulSoup transforms complex HTML documents into a complex tree of Python objects. Here's an example HTML document:

html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>
<h3><b id='boldest'>Lebron James</b></h3>
<p>Salary: $92,000,000</p>
<h3>Stephen Curry</h3>
<p>Salary: $85,000,000</p>
<h3>Kevin Durant</h3>
<p>Salary: $73,200,000</p>
</body>
</html>
You can parse it using BeautifulSoup:


from bs4 import BeautifulSoup

html = """
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>
<h3><b id='boldest'>Lebron James</b></h3>
<p>Salary: $92,000,000</p>
<h3>Stephen Curry</h3>
<p>Salary: $85,000,000</p>
<h3>Kevin Durant</h3>
<p>Salary: $73,200,000</p>
</body>
</html>
"""
soup = BeautifulSoup(html, "html.parser")
print(soup.prettify())
Tags and Navigable Strings
Tags are used to navigate through the HTML document. For example, to get the title:

tag_object = soup.title
print("tag object:", tag_object)
print("tag object type:", type(tag_object))
Children, Parents, and Siblings
You can navigate the HTML tree using children, parents, and siblings:

tag_child = tag_object.b
parent_tag = tag_child.parent
sibling_1 = tag_object.next_sibling
HTML Attributes
Access attributes of a tag like a dictionary:

tag_child = soup.find(id='boldest')
print(tag_child['id'])  # Output: boldest
Finding Elements
Use find_all() to find all occurrences of a tag:


table_rows = soup.find_all('tr')
for row in table_rows:
    print(row)
Scraping Web Content
Download and parse a webpage:


import requests
url = "http://www.ibm.com"
data = requests.get(url).text
soup = BeautifulSoup(data, "html.parser")

for link in soup.find_all('a', href=True):
    print(link
just creat simple read me
ChatGPT
Sure, here's a simple README.md for your web scraping lab project:


# Web Scraping Lab

This repository contains a web scraping lab using Python and the BeautifulSoup library. The lab demonstrates how to scrape data from web pages, parse HTML, and extract useful information.

## Objectives

After completing this lab, you will be able to:
- Parse HTML documents using BeautifulSoup.
- Navigate HTML documents and extract data.
- Use BeautifulSoup to find specific elements by tag, class, id, and more.
- Scrape web content and convert it into pandas DataFrames for analysis.

## Installation

To install the required libraries, run the following commands:

```bash
!mamba install bs4==4.10.0 -y
!pip install lxml==4.6.4
!mamba install html5lib==1.1 -y
!pip install requests==2.26.0
Usage
Import Libraries:


from bs4 import BeautifulSoup
import requests
import pandas as pd
Parse HTML Content:


html = """
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>
<h3><b id='boldest'>Lebron James</b></h3>
<p>Salary: $92,000,000</p>
<h3>Stephen Curry</h3>
<p>Salary: $85,000,000</p>
<h3>Kevin Durant</h3>
<p>Salary: $73,200,000</p>
</body>
</html>
"""
soup = BeautifulSoup(html, "html.parser")
print(soup.prettify())
Scrape a Web Page:


url = "http://www.ibm.com"
data = requests.get(url).text
soup = BeautifulSoup(data, "html.parser")

for link in soup.find_all('a', href=True):
    print(link.get('href'))
Convert Scraped Data to DataFrame:


url = "https://example.com/table"
data = requests.get(url).text
soup = BeautifulSoup(data, "html.parser")
table = soup.find('table')

rows = []
for row in table.find_all('tr'):
    cells = row.find_all('td')
    rows.append([cell.text for cell in cells])

df = pd.DataFrame(rows, columns=['Column1', 'Column2', 'Column3'])
print(df)

License
This project is licensed under the MIT License.

Feel free to customize this template further based on your specific needs and details of the lab.
