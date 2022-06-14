1. JavaScript로 팝업 출력

	```
	window.open(url, "팝업", "width=1600, height=1000, left=0, top=0");
	```

2. IE에서는 스크롤바가 기본값이 아니기때문에 옵션값을 추가해야한다.

	```
	scrollbars=1 추가

	window.open(url, "자세히보기", "width=1600, height=1000, left=0, top=0, scrollbars=1");
	```