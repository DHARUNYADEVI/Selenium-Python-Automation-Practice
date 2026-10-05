# Selenium Python Automation Practice
## Name: Dharunyadevi S
## Register Number:212223220018
This repository contains three beginner-level automation activities performed using **Python and Selenium WebDriver**. These activities helped me practice browser automation, element identification, locators, explicit waits, and handling real-world website interactions.

## Activities

### 1. Automating Google Search for Actor 

In this activity, Selenium was used to automate a Google search.

The automation performs the following steps:

* Opens Google Chrome
* Navigates to Google
* Identifies the search box using Selenium
* Enters `actor surya`
* Submits the search
* Waits for the search results page

This activity provided practice with:

* `webdriver`
* `By.NAME`
* `send_keys()`
* `submit()`
* Browser navigation
```py
from selenium import webdriver
from selenium.webdriver.common.by import By
import time
driver = webdriver.Chrome()
driver.get("https://www.bing.com")
search_box = driver.find_element(By.NAME, "q")
search_box.send_keys("Actor Surya")
search_box.submit()
time.sleep(5)
driver.quit()
```
## Output
<img width="777" height="442" alt="image" src="https://github.com/user-attachments/assets/5648b96a-818e-4796-a9cc-744da0d6b085" />

### 2. Finding Elements in SauceDemo

In this activity, Selenium was used with the SauceDemo website to practice different types of element locators.

The automation identifies elements such as:

* Username field
* Password field
* Login button
* Product names
* Add-to-cart elements

Different Selenium locator strategies were practiced, including:

* ID
* CSS Selector
* XPath
* Class Name
* Name
* Tag Name
* Link Text
* Partial Link Text

The activity also demonstrated the difference between:

```python
find_element()
```

and

```python
find_elements()
```

`find_element()` is used when a single matching element is required, while `find_elements()` returns multiple matching elements.
```py
from selenium import webdriver
from selenium.webdriver.common.by import By
import time
driver=webdriver.Chrome()
driver.get("https://www.saucedemo.com/")
username=driver.find_element(By.ID,"user-name")
username.send_keys("standard_user")
password=driver.find_element(By.ID,"password")
password.send_keys("secret_sauce")
login=driver.find_element(By.ID,"login-button")
login.click()
elements=driver.find_elements(By.CLASS_NAME,"inventory_item_name ")
length=len(elements)
print("Number of elements: ",length)
for e in elements:
    print(e.text)
driver.quit()
```
## Output
<img width="782" height="192" alt="image" src="https://github.com/user-attachments/assets/935d04ef-3ac8-4002-a7ec-47f18c3da0d5" />

### 3. Flipkart Login Automation

This activity focused on automating the initial stages of the Flipkart login process.

The automation:

* Opens Flipkart
* Maximizes the browser window
* Handles the initial page state
* Locates the Login option
* Clicks the Login button
* Locates the mobile number field
* Accepts the mobile number from the terminal
* Enters the mobile number into the Flipkart login field
* Allows OTP completion manually

Explicit waits were used to make the automation more reliable.
The mobile number field was located using XPath:
The OTP step is completed manually because OTP/CAPTCHA verification should not be bypassed or automated.
```py
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
driver = webdriver.Chrome()
driver.get("https://www.flipkart.com/")
driver.maximize_window()
wait = WebDriverWait(driver, 15)
driver.find_element(By.TAG_NAME, "body").send_keys(Keys.ESCAPE)
login = wait.until(
    EC.element_to_be_clickable((By.XPATH, '//span[text()="Login"]'))
)
login.click()
mobile_number = input("Enter the mobile number: ")
mobile = wait.until(
    EC.visibility_of_element_located((By.XPATH, '//*[@id="1"]'))
)
mobile.clear()
mobile.send_keys(mobile_number)
print("Complete OTP manually in Chrome.")
input("After completing OTP, press Enter in this terminal...")
print("Flipkart logged in successfully")
driver.quit()
```
## Output
<img width="777" height="130" alt="image" src="https://github.com/user-attachments/assets/364429f0-9041-4c52-af63-635cb3ead66c" />


## Technologies Used

* Python
* Selenium WebDriver
* Google Chrome
* ChromeDriver
* XPath
* CSS Selectors

## Key Learning

Through these three activities, I practiced how to:

* Launch and control a browser using Selenium
* Navigate between web pages
* Identify web elements
* Work with different locator strategies
* Enter data into input fields
* Click buttons and links
* Retrieve multiple elements
* Use explicit waits
* Handle dynamic web pages
* Understand common Selenium exceptions
* Perform basic web automation on real websites

These activities were created for **learning and practicing Selenium automation**. Login verification steps such as OTP and CAPTCHA are intentionally completed manually.
