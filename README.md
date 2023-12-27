## Web Scraper using Selenium

A simple web scraper using Selenium. 

The purpose of this project is to demonstrate the scraping capabilities of Selenium for dynamically loading pages. In this case, the blog section of the Rize reviews website wherein the blog category page is being loaded as an 'infinite scrolling' feature instead of pagination.

### Usage
Customize the scraper by modifying the rize-scraper.ipynb (jupyter notebook) file:

```python
blog_link = []
blog_title = []
blog_auth = []
blog_date = []

url = "https://rizereviews.com/blog/"

chrome_options = webdriver.ChromeOptions()
driver = webdriver.Chrome(chrome_options)
```
Change the URL variable to a desired page that you would like to scrape

```python
# Find all blog links
blogs = driver.find_elements(
    By.CSS_SELECTOR,
    ".fl-post-grid-post",
)

for blog in blogs:
    blog_title.append(blog.find_element(By.TAG_NAME, "h2").text)
    blog_link.append(blog.find_element(By.TAG_NAME, "a").get_attribute("href"))
    blog_auth.append(blog.find_element(By.CLASS_NAME, "fl-post-grid-author").text)
    blog_date.append(blog.find_element(By.CLASS_NAME, "fl-post-grid-date").text)
```
Following this, update the selector of the elements that you need to scrape.

### Requirements

- Selenium
- Pandas
- Time

### Contributing

Pull requests are welcome. Feel free to submit improvements or enhancements.
