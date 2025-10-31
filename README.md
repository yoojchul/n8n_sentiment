# An n8n example using naver API, web crawling, sentiment analysis and google sheet to show the emotion tone of news article about a keyword

n8n과 openAI를 이용해서 특정 키워드에 대한 기사를 검색하고 기사가 해당 키워드에 대한 긍정, 중립, 부정인지 판별합니다. workflow는 n8n를 사용해서 naver API를 통해 특정 keyword에 관한 뉴스 기사를 검색하고 오늘 날짜로 된 기사를 웹크로링으로 전문을 모두 가져 옵니다.  그리고 <body>에 포함된 text만 뽑아 sentiment analysis에 넘깁니다. sentiment analysis에는 OpenAPI를 이용합니다. Positive, Neutral 그리고 Negative를 따로 count하는 java script를 거쳐서 Google sheet에 count 수를 기록합니다.   "My-workflow.json" 파일로 된 workflow을 n8n에서 import하면 아래 화면을 볼 수 있습니다. 

![Alt text](images/overall.png)
  
실행에는 서비스 접속을 위한 ID가 각각 필요합니다.  Naver API에는 X-Naver-Client-Id와 X-Naver-Client-Secret를 입력해야 합니다.

![Alt text](images/naver.png)

(https://developers.naver.com/docs/serviceapi/search/news/news.md  참조)


OpenAI에는 API key가 있어야 하고 

![Alt text](images/openai.png)

(https://platform.openai.com/api-keys  참조)

그리고 Google sheet 사용을 위한 credential은 service account로 만듭니다. 

![Alt text](images/google.png)

마지막 google sheet 지정을 위해 ID가 필요한데 URL에서 볼 수 있습니다

![Alt text](images/google_sheet2.png)

ID는 Document에 "By ID"로 지정하고 구글 드라이브에서 해당 파일의 공유 특성도 "편집자"로 변경해야 "시트1"를 볼 수 있고 편집이 가능합니다. 

![Alt text](images/google_sheet.png)

Webhook1는 아래 명령어로 시작합니다. 

\# curl -d "keyword=LG화학"  -H "Content-Type: application/x-www-form-urlencoded" -X POST http\://localhost:5678/webhook-test/4b71a486-e711-4de0-a721-462c92bcc540









