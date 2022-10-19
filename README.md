from selenium import webdriver

from webdriver_manager.chrome import ChromeDriverManager

import time



meeting_url = "https://v.ringcentral.com/join/315564510467?pw=18c0ddcb14a35a5a7d2433e57a02184d"


options = webdriver.ChromeOptions()

options.add_experimental_option("prefs", {
    "profile.default_content_setting_values.media_stream_mic": 2,
    "profile.default_content_setting_values.media_stream_camera": 2,
    "profile.default_content_setting_values.geolocation": 1,
    "profile.default_content_setting_values.notifications": 1,
    "protocol_handler.excluded_schemes.hcp": 1,
    "profile.password_manager_enabled": False,
    "credentials_enable_service": False
})

options.add_experimental_option("excludeSwitches", ['enable-automation'])

options.add_argument(
    "--user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.77 Safari/537.36")

options.add_argument("--use-fake-ui-for-media-stream")

browser = webdriver.Chrome(ChromeDriverManager(cache_valid_range=365).install(), options=options)

browser.implicitly_wait(7)

browser.get(meeting_url)


while True:
    time.sleep(5)
    print("beating")
