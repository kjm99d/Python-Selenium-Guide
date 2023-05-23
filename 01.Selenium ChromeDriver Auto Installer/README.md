# 01.Selenium ChromeDriver Auto Installer

파이썬 셀레니움을 매번 크롬 브라우저 버전에 맞춰서 수정해줘야하는 경우가 빈번하다.

이 코드는 위와 같은 상황에서 사용하기 적합한 코드이다.



## 설치 명령어

```bash
pip install selenium
pip install chromedriver_autoinstaller
```

## 예제 코드
```python
from selenium import webdriver
import chromedriver_autoinstaller
import os

# Check if chrome driver is installed or not
chrome_ver = chromedriver_autoinstaller.get_chrome_version().split('.')[0]
driver_path = f'./{chrome_ver}/chromedriver.exe'
if os.path.exists(driver_path):
    print(f"chrom driver is insatlled: {driver_path}")
else:
    print(f"install the chrome driver(ver: {chrome_ver})")
    chromedriver_autoinstaller.install(True)

# Get driver and open url
driver = webdriver.Chrome(driver_path)
driver.get("https://google.com")
```