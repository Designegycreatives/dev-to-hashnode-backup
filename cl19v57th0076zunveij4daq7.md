## Playstore Web Scraping With Python

[Download Jupyter Notebook Here](https://jovian.ai/designegycreatives/data-analysis-fintech-project)

[GitHub Reference ](https://github.com/Designegycreatives/Fintech-In-Nigeria-Analysis)

#### Last Month I did a webscraping project after learning from the C.E.O of [Jovian](https://jovian.ai), how to webscrape data from websites using python programming.

#### So I thought i could share my personal web scraping project.

#### My project is all about a data analysis project that involved data scraping from Playstore and i chose the Nigeria FINTECH Business Niche as my focal point.

**Step 1:**
I scraped my data from google play store using selenium and chrome manager driver.

#### Importing `Necessary Libraries`

```
import time
from selenium import webdriver
from webdriver_manager.chrome import ChromeDriverManager
``` 
#### Accessing `PlayStore` Using `Selenium`

```
driver = webdriver.Chrome(ChromeDriverManager().install())
driver.get('https://play.google.com/store/search?q=fintech%20in%20nigeria&c=apps')
time.sleep(10)
``` 
#### Getting All `The Apps` In The Required Page

```
SCROLL_PAUSE_TIME = 5
 
# Get scroll height
last_height = driver.execute_script("return document.body.scrollHeight")
time.sleep(SCROLL_PAUSE_TIME)
 
while True:
    # Scroll down to bottom
    driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
 
    # Wait to load page
    time.sleep(SCROLL_PAUSE_TIME)
 
    # Calculate new scroll height and compare with last scroll height
    new_height = driver.execute_script("return document.body.scrollHeight")
    if new_height == last_height:
        break
    last_height = new_height
``` 
#### `Scraping` App Links

```
links_fintech = []
elems = driver.find_elements_by_xpath("//a[@href]")
for elem in elems:
    if "details?id" in elem.get_attribute("href"):
        links_fintech.append((elem.get_attribute("href")))
        
links_fintech = list(dict.fromkeys(links_fintech))
``` 
#### Scraping The `Necessary Information` From Each App

```
list_all_elements = []
for iteration in links_fintech:
    try:
        driver.get(iteration)
        print(iteration)
        time.sleep(3)
 
        header1 = driver.find_element_by_tag_name("h1")
        
        downloads = driver.find_elements_by_class_name("htlgb")
        list_downloads = []
        for x in range (len(downloads)):
            if x % 2 == 0:
                list_downloads.append(downloads[x].text)
    

        titles = driver.find_elements_by_class_name("AHFaub")
        comments = driver.find_element_by_class_name("EymY4b")
 
        list_elements = [iteration,header1.text, list_downloads.append(downloads[x].text), comments.text.split()[0]]
        for x in range (len(titles)):
            if titles[x].text == "Download":
                list_elements.append(list_others[x])
            if titles[x].text == "Developer":
                for y in list_others[x].split("\n"):
                    if "@" in y:
                        list_elements.append(y)
                        break
 
        list_all_elements.append(list_elements)
    except Exception as e:
        print(e)
``` 
#### Creating `A CSV File` For `Scraped DataFrame`

```
import pandas as pd
 
df = pd.DataFrame(list_all_elements,columns=['URL', 'Name', 'downloads', 'install']) 
df_1 = df.to_csv('fintech_playstore.csv', header = True, index=False, encoding="utf-8")
``` 

```
df_1
``` 
You can download the dataset from my GitHub Reference 

**Then i visualized my data Using PowerBI**

![image 1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1648420685578/hRS6dw0k7.jpg)

[Reference 01](https://www.danielherediamejias.com/scraping-google-play-store-with-python-and-selenium/)

[Reference 02](https://play.google.com/store/search?q=fintechs%20in%20nigeria&c=apps)




