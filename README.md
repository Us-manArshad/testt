from selenium import webdriver

from webdriver_manager.chrome import ChromeDriverManager

import time



meeting_url = "https://v.ringcentral.com/join/570144341444?pw=0488a2bf0f0024bbc23e5f58c5fc3e38"

options = webdriver.ChromeOptions()

options.add_experimental_option("prefs", {
    "profile.default_content_setting_values.media_stream_mic": 1,
    "profile.default_content_setting_values.media_stream_camera": 1,
    "profile.default_content_setting_values.geolocation": 1,
    "profile.default_content_setting_values.notifications": 1,
    "protocol_handler.excluded_schemes.hcp": 1,
    "profile.password_manager_enabled": False,
    "credentials_enable_service": False
})

options.add_experimental_option("excludeSwitches", ['enable-automation'])

browser = webdriver.Chrome(ChromeDriverManager(cache_valid_range=365).install(), options=options)

browser.implicitly_wait(7)

browser.get(meeting_url)


while True:

    time.sleep(5)

    print("beating")

