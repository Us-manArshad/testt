from selenium import webdriver

from webdriver_manager.chrome import ChromeDriverManager
from webdriver_manager.core.utils import ChromeType

import time



meeting_url = "https://v.ringcentral.com/join/315564510467?pw=18c0ddcb14a35a5a7d2433e57a02184d"

options = webdriver.ChromeOptions()

options.add_experimental_option("prefs", {
    "profile.default_content_setting_values.media_stream_mic": 1,
    "profile.default_content_setting_values.media_stream_camera": 1,
    "profile.default_content_setting_values.geolocation": 1,
    "profile.default_content_setting_values.notifications": 1,
    "credentials_enable_service": False,
    "profile.password_manager_enabled": False
})

options.add_argument(
    "--user-agent=Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.0.0 Safari/537.36")

browser = webdriver.Chrome(executable_path=ChromeDriverManager(cache_valid_range=365, chrome_type=ChromeType.CHROMIUM).install(), options=options)

browser.implicitly_wait(7)

browser.get(meeting_url)


while True:
    time.sleep(5)
    print("beating")
