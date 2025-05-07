# Wikipedia-scraping-python
is a Python script that demonstrates how to scrape Wikipedia pages using keywords. This script uses the wikipedia-api library to fetch the content of Wikipedia pages.

pip install wikipedia-api

import wikipediaapi

def fetch_wikipedia_content(keyword):
    wiki_wiki = wikipediaapi.Wikipedia('en')
    page = wiki_wiki.page(keyword)

    if page.exists():
        print(f"Title: {page.title}")
        print(f"Summary: {page.summary[:500]}...")  # Print the first 500 characters of the summary
        return page.text
    else:
        print(f"The page for '{keyword}' does not exist.")
        return None

# Example usage
keyword = "Python (programming language)"
content = fetch_wikipedia_content(keyword)

if content:
    with open(f"{keyword.replace(' ', '_')}.txt", "w", encoding="utf-8") as file:
        file.write(content)
    print(f"Content saved to {keyword.replace(' ', '_')}.txt")
