
데이터 크롤링 프로젝트
====================================
 
 - 이희재, 안효준
 
- 데이터 수집의 개요
   - 수집 동기, 목적
      - 차량 공유 서비스가 활성화 되면서 '타다'와 '카카오 택시'로 사회에 많은 논란이 있었다. '카카오 택시'는 기존 택시 업계와의 상생 협약을 맺으며 사업을 진행하고 있다. 반면 타다는 업계와의 갈등이 계속되며 타다 금지법이 국회에서 통과 되었다. 법 통과 이후에도 혁신과 불법이라는 극단적인 의견이 대립되고 있다.
      - 유튜브 저널리즘이 본격화되면서 영향력이 종이신문과 TV, 포털과 비교되는 수준을 향하고 있다. 최근 TV보다 모바일 기기를 활용한 영상 시청 시간이 증가하고 있다. 네이버와 다음은 텍스트 기사 바탕으로 댓글이 주로 서비스 되고 있고 두 사이트의 댓글은 성향에 따라 극단적으로 나눠지는 것으로 파악되고 있다(1). 유튜브에서 댓글 성향 분석이 활발하게 이루어지고 있다. 최근 이슈가 되고 있는 '타다 금지법' 관련 동영상 댓글 수집과 분석을 진행하고자 한다.
      
- 데이터 수집의 계획 및 주기 작성

![KakaoTalk_20200313_043617368](https://user-images.githubusercontent.com/15780961/76589847-c7033a80-652e-11ea-9f94-960d9f0b3b03.png)
   - 
- 데이터를 수집하는 시스템의 구조도 및 프로세스 등을 설명
- 크롤링하는 방법
   - AWS 서버를 사용하여 YouTube '타다 금지법' 개별 영상 댓글 크롤링
   - 스크래피 프레임워크 사용

- 데이터의 저장
   - mongodb 데이터 베이스에 크롤링 데이터 저장
   - 3월 17일 이전 3월 데이터 저장
   - 

- 코드의 관리
   - github 서비스를 이용해서 코드 관리, 공유, 이슈처리
      - master repo : Heejae
   - 설치되어야 하는 패키지는 requirements.txt로 작성
      - import requests
      - import time
      - import scrapy
      - from selenium import webdriver
      - from selenium.webdriver.chrome.options import Options
      - from selenium.webdriver.common.keys import Keys
      - from scrapy.http import TextResponse
      - from PIL import Image as pil
      - from konlpy.tag import *  
      - from wordcloud import WordCloud

     - import matplotlib
     - import matplotlib.pyplot as plt
     - from matplotlib import font_manager, rc

     - from collections import Counter 
     - import pandas as pd

     - import pymongo
     - import sys

     - from wordcloud import WordCloud, STOPWORDS, ImageColorGenerator


     - import nltk 
     - from nltk.probability import FreqDist 
     - import matplotlib as mpl

     - from konlpy.tag import Hannanum
     - import re
     - import csv
     - from apyori import apriori
     - import networkx as nx

   - 코드의 설명은 처음 접한 사람도 그대로 따라하면 코드를 실행 할수 있을 정도로 간결하게 작성
      - 주석 작성, 우리가 하면 다 할 수 있다.
      
- 결론

      - 형태소 분석 결과
      - 예상과 달리, '타다' 단어 언급 빈도가 저조
      - 이유: KoNLPy 패키지에서 '타다'를 동사로 인식하여, 분류 오류 발생.
          - '타다는' -> '타' + '다는'
          - '타다' -> '타' + '다'
      - 워드 클라우드 분석 결과
      
         - 택시, 불법, 기사, 혁신 등이 많이 언급 되었음.
         - 중간 발표 때, '타다'는 불법이라고 하는 여론과, 혁신적이라고 하는 여론이 양립되어 있을 것으로 예상하였다.
         - 크롤링 개별 영상 댓글에서 유튜브 댓글 트렌드를 확인한 결과, '불법'과 '혁신'이라는 단어의 빈도 수가 높은 것으로 관찰되었다.
- 단어 별 네트워크 분석 결과

      - 이철희, 채이배 의원: 언급 빈도가 많고, 두 사람에 대한 연관성이 있는 것으로 보임.
      - 실제로, 두 의원이 주도하여 타다 금지법 법사위 통과 반대한 것으로 확인.
         

      - 자연어 처리와 텍스트 마이닝을 사용하여 댓글 성향 분석
      
      
- 참고문헌
- (1) 수집동기 : 이준기, 한미애. (2012). 개인의 정치성향이 뉴스 댓글에 대한 신뢰성과 사회적 영향력의 인식에 미치는 영향. 한국전자거래학회지, 17(1), 173-187.