# 02.Find Elements

파이썬 셀레니움 사용시 브라우저 렌더링이 완료된 이후, 각 DOM 요소를 찾는 방법이다.



## 1. 셀레니움 브라우저 열기

```python
from selenium import webdriver

"""
' 기타 드라이버 로딩 코드들 ... 
'
'
'
"""

# Get driver and open url
driver = webdriver.Chrome()
driver.get("https://google.com")
```



## 2. 셀레니움을 통한 브라우저에서 DOM 요소 찾기

### DOM 예제

    <script type="text/plain" id="ad-timeboard-response" data-gfp-banner-size="830x130" data-gfp-banner-type="full">

아래 작성되는 다양한 방법들에 대해서는 위 예제를 기반으로 진행된다.

### 기본적으로 사용되는 모듈

```
from selenium.webdriver.common.by import By # 필요한 모듈
```

위 모듈을 기반으로하여 요소를 찾는다.

By.CLASS_NAME, By.TAG_NAME 과 같은 속성들을 제공해주기 때문에, 해당 속성값과 일치하는 DOM 요소를 찾을 수 있다.



- ID를 기반으로 찾는 방법

  ```python
  from selenium.webdriver.common.by import By # 필요한 모듈
  
  elem_script = driver.find_element(By.ID, "ad-timeboard-response")

- 속성값으로 찾는 방법

  ```python
  from selenium.webdriver.common.by import By # 필요한 모듈
  elem_script = driver.find_element(By.CSS_SELECTOR, '[data-gfp-banner-size="gfp-banner-size="830x130"]')
  ```

- 여러개의 요소를 찾는 방법

  일반적으로 DOM 에는 동일한 이름의 태그를 볼 수 있다.

  이러한 태그 같은 경우 태그명이 중첩되는 경우가 대다수 존재한다.

  이때 이러한 중첩되는 DOM 요소들을 리스트형태로 수집할 수 있는 방법이다.

  ```python
  from selenium.webdriver.common.by import By # 필요한 모듈
  
  elem_scripts = driver.find_element(By.TAG_NAME, "script")
  for elem_script in elem_scripts:
      print(elem_script)
  ```

