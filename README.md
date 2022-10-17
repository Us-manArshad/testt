from selenium import webdriver

from selenium.webdriver.firefox.options import Options

from webdriver_manager.firefox import GeckoDriverManager

import time



meeting_url = "https://v.ringcentral.com/join/638640508770?pw=0af436f88fcdbd054d4e5a9f14c0b7b8"

options = Options()

options.add_argument("-–disable-blink-features")

options.add_argument("-–disable-notifications")

options.set_preference("permissions.default.microphone", 2)

options.set_preference("permissions.default.camera", 2)

options.set_preference("media.navigator.permission.disabled", True)

options.add_argument(
    "--user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.77 Safari/537.36")

browser = webdriver.Firefox(executable_path=GeckoDriverManager(cache_valid_range=365).install(), options=options)

browser.implicitly_wait(7)

browser.get(meeting_url)


while True:
    time.sleep(5)
    print("beating")
