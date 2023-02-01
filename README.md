








## Jsoup 사용방법
태그명 : 태그이름으로 접근
	
select("div") : div 태그를 모두 선택
.이름 : 태그의 속성의 이름이 class 인 것중에서 속성의 값이 이름과 같은것
select(".a") : 태그의 class="a"인 모든 태그를 선택

#값 : 태그의 속성의 이름이 id 인 것중에서 속성의 값이 #뒤의 값과 같은것
select("#a") : 태그의 id="a"인 모든 태그를 선택

a b : a 태그의 자식 태그중에서 b 태그를 모두 선택 (a 태그의 자손 태그까지 모두 선택)
a > b : a 태그의 자식 태그중에서 b 태그를 모두 선택 (a 태그의 바로 밑에 있는 자식만 선택)
select("a b")
select("a > b")
			a
		b		c
	c	d		d	b
select("table > tr td > img.a") : table 밑에 있는 img 클래스 이름이 a 인것 선택 (실제로는 tbody 경로 적어줘야 함)

태그의 속성으로 접근하기
: 태그명[속성명=값]
: 태그명[속성명^=값] : 값으로 시작하는 것
	a[href ^= http]
: 태그명[속성명$=값] : 값으로 끝나는 것
	img[src $= jpg]
: 태그명[속성명*=값] : 값이 포함하는 것
	img[src *= flower]

---------------------------------


 Jsoup도 간편하게 사용할 수 있어서 좋지만, 동적 웹페이지를 크롤링하는데 적합하지 않다. 그리고, XPath를 지원하지않기 때문에 별도의 라이브러리를 필요로 한다. 이 두 개의 단점을 커버할 수 있는 것이 바로 Selenium이다.

 Selenium은 웹 어플리케이션 테스트를 자동화 할 때 사용하는 툴이다. WebDriver를 통해 웹 브라우저가 실행되며 미리 작성된 스크립트를 통해 사용자가 직접 조작하는 듯한 모습을 눈으로 직접 확인할 수 있다. 또한, 현재 브라우저에 출력된 페이지의 소스를 파싱 할 수 있다.

 Jsoup과 Selenium을 비교해보면 이렇다.

 Jsoup은 백그라운드에서 HTTP Request/Response가 이루어지며, Request를 던졌을 때 웹 서버에서 응답한 결과를 받아온다. 따라서, 서버 사이드 랜더링(SSR, Server-Side Rendering)을 사용하는 웹 사이트는 서버에서 랜더링을 한 후 화면을 그리기 때문에 크롤링이 가능하지만, 클라이언트 사이드 랜더링(CSR, Client-Side Redering)을 사용하는 웹 사이트는 최소한의 페이지만 서버에서 랜더링하고 클라이언트(브라우저)에서 나머지 화면을 랜더링하기 때문에 HTTP Request로는 실제 브라우저에서 보여지는 화면을 스크랩 할 수 없다. 하지만, Selenium은 현재 브라우저에 출력된 페이지의 소스를 파싱 할 수 있다는 특성을 이용하여 CSR을 사용하는 웹 사이트도 크롤링 할 수 있다. 또한, XPath를 지원하고 Javascript 명령어를 실행할 수 있기 때문에 Jsoup보다 많은 데이터를 크롤링 할 수 있다.

 Selenium을 이용한 크롤러가 Jsoup보다 마냥 좋은 것은 아니다. Jsoup은 HTTP Request를 통해 웹서버에 직접 요청하기 때문에 빠른 응답을 받을 수 있다. 하지만, Selenium은 브라우저가 랜더링 된 후 페이지를 파싱하기 때문에 수집 속도가 느리다. 따라서, 동적 웹페이지가 아니라면 Jsoup을 이용하는 것이 좋다.



---------------------------------------

Selenium 가이드
[셀레니움 예시](https://velog.io/@joyoo1221/%EC%9E%90%EB%B0%94-%EC%85%80%EB%A0%88%EB%8B%88%EC%9B%80selenium%EC%9C%BC%EB%A1%9C-%ED%81%AC%EB%A1%A4%EB%A7%81%ED%95%98%EA%B8%B0-1)
[셀레니움 가이드](https://www.selenium.dev/documentation/webdriver/elements/finders/)
