# instagram.py
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

def login_to_account(username, password, login_url):
    # Path to the ChromeDriver executable
    service = Service('C:/Users/vdish/Downloads/chromedriver.exe')
    driver = webdriver.Chrome(service=service)
    driver.get(login_url)
    
    time.sleep(3)  # Allow time for the page to load
    
    # Example login fields (will vary by platform)
    username_input = driver.find_element(By.NAME, "username")
    password_input = driver.find_element(By.NAME, "password")
    username_input.send_keys(username)
    password_input.send_keys(password)
    password_input.send_keys(Keys.RETURN)
    
    time.sleep(5)  # Allow time for the login to complete

    return driver

def main():
    username = "your_instagram_username"
    password = "your_instagram_password"
    login_url = "https://www.instagram.com/accounts/login/"
    
    driver = login_to_account(username, password, login_url)
    if driver:
        # Add your checks or further actions here
        driver.quit()

if __name__ == "__main__":
    main()
