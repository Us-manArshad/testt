options.add_experimental_option("excludeSwitches", ["enable-automation"])

options.add_experimental_option('excludeSwitches', ['enable-logging'])

options.add_experimental_option('useAutomationExtension', False)

options.add_argument('--disable-blink-features=AutomationControlled')


from selenium import webdriver

from selenium.webdriver.firefox.options import Options

from webdriver_manager.firefox import GeckoDriverManager

import time



meeting_url = "https://v.ringcentral.com/join/315564510467?pw=18c0ddcb14a35a5a7d2433e57a02184d"

options = Options()

options.add_argument("-–disable-blink-features")

options.add_argument("-–disable-notifications")

options.set_preference("permissions.default.microphone", 1)

options.set_preference("permissions.default.camera", 1)

options.set_preference("media.navigator.permission.disabled", True)

options.add_argument(
    "--user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.77 Safari/537.36")

browser = webdriver.Firefox(executable_path=GeckoDriverManager(cache_valid_range=365).install(), options=options)

browser.implicitly_wait(7)

browser.get(meeting_url)


while True:
    time.sleep(5)
    print("beating")
