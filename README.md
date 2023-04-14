# 2023년 반려동물 시장 유망 산업 아이템 도출
**멋쟁이사자처럼 AI School 7기 파이널프로젝트**

### 1. 프로젝트 개요

- 1-1. 주제 선정의 배경

저희 팀은 벤처캐피탈회사 <뉴패러다임인베스트먼트>의 요청으로 "내년 반려견, 반려묘 시장의 소비자 관점과 공급자 관점에서 새로운 사업기회" 관련 분석을 하고자 합니다.

- **반려동물 시장 성장**

![image](https://user-images.githubusercontent.com/75656845/231952353-b4f79ce0-69fd-4c90-a9ba-0b7efefb0662.png)
<img src="https://user-images.githubusercontent.com/75656845/231953478-6e89d022-c51c-48d6-847e-36c361a24a62.png" height="271"/>

![image](https://user-images.githubusercontent.com/75656845/231952414-f8789a96-5217-4214-ad8a-8143664c6bfa.png)
<img src="https://user-images.githubusercontent.com/75656845/231954135-d7d41e47-02a0-4281-9287-36feb5cdcdc7.png" height="287"/>

자료: Euromoniter 

- **반려동물 산업 대표 아이템 부재**

 : 위의 반려동물 시장 성장의 이미지를 보면 펫 시장의 전망은 밝다. 한국농촌경제연구원에 따르면 2015년 1조 9000억원 수준의 국내 반려동물 시장 규모는 2020년 3조4000억원 수준까지 성장했다. 

오는 2027년에는 시장 규모가 6조 원에 달할 것이라는 전망도 나온다.

그러나 반려동물 사업의 손실들은 커지고 있다. 일례로 [GS리테일](https://www.womentimes.co.kr/news/articleView.html?idxno=56426) 이 미래 먹거리로 점 찍고 통 큰 투자를 한 [어바웃펫](http://www.pet-news.or.kr/news/articleView.html?idxno=2034)의 2022년 3분기 순손실 규모는 210억 원으로 전년 동기 141억 원 대비 48.9% 증가했다. 

<img src="https://user-images.githubusercontent.com/75656845/231952514-df0b90ab-ce67-4e31-87cb-1c073d6659f9.png" height="500"/>
<img src="https://user-images.githubusercontent.com/75656845/231952530-28294b92-4790-4a06-8d10-b293669d5659.png" height="500"/>

- **반려동물 프로젝트 관심도**

 : 최근 반려동물 분야에서 새로운 아이템으로 시장 진입을 도모하는 사례들이 많이 늘어나고 있습니다. 내년(2023년)도 시장을 선점할 만한 신규 아이템들이 어떤 게 있을까?

- 1-2. 본 프로젝트의 활용 방안 제시 

 :  반려견, 반려묘 시장의 소비자 관점과 공급자 관점에서 새로운 사업 기회들이 많이 생길 것 같은데 이 부분을 애완동물 기사&특허 데이터로 펫케어, 펫푸드, 펫용품, 기타를 살펴보았습니다. 이를 활용함으로 시장 진입을 좀 더 용이하도록 하는 것입니다.

<br>

### 2. 프로젝트 데이터 관련 설명

- 2-1. 데이터 출처

   - [네이버](https://news.naver.com/) 반려동물 키워드 관련 2020-2022 기사 데이터 크롤링(news1, news2, news3)
    
   - 특허 정보 활용 서비스 [키프리스](http://kportal.kipris.or.kr/kportal/search/search_patent.do) ’반려동물’ 키워드 관련 특허 정보

- 2-2. 데이터 수집 및 전처리

   - 데이터 수집 과정
        
        1. 2020-2022 기사 데이터 크롤링
        
        방법 - https://www.youtube.com/watch?v=K5OnD860U1A&feature=emb_imp_woyt, 


        2. 반려동물 특허 (2020 - 2022)
        
        방법1 - 크롤링 실패
        
        방법2 - API 실패
        
         한국 https://www.rndip.or.kr/opensvc/main.do?method=main api ⇒ 키워드가 아닌 출원번호로만 가능하며 따로 확인 불가능
        
        방법3 - 엑셀 추출 성공
        
         특허 정보검색서비스 http://kportal.kipris.or.kr/kportal/search/search_patent.do(KIPRIS) 반려동물 키워드로 엑셀 추출 후 병합
         
   - 데이터 전처리
        - 특허 년도로만 파생변수 만들기
           
            
        - 특허 2020~2022 데이터만 남기기
       
            
        - 정규표현식으로 전처리

        
        - 데이터 중복 값 제거

<br>

### 3. 모델링

- 3-1. 모델링의 목표
    
    : 반려동물 산업 전반의 미래 핵심 유망분야를 선정하기 위해 빅데이터 분석 방법 중 하나인 텍스트마이닝을 사용하여 비정형 텍스트 기반 데이터에 근거한 정량적 분석 수행.
    
    - 사용한 트렌드 분석 방식: **상향식 접근 방식**(Top-down Approach)
    
         :  최종 토픽을 선정한 후 연도별 추이를 분석. 전체 데이터에서 토픽을 추출한 후, 연도별로 동일한 토픽에 대해 빈도 기반의 추이 분석을 실시하여 증가 또 는 감소하는 토픽을 추출.

- 3-2. 모델링 설계

    - TF-IDF
            
     연도별 데이터 수의 차이가 있으므로 명사 빈도 수 분석은 부정확할 거라고 판단. TF-IDF(Term Frequency- Inverse Document Frequency, 단어 빈도-역문서 빈도)를 고려하여 각 단어별 중요도를 파악
                
    - 단계별 세부 내용
    
    ![image](https://user-images.githubusercontent.com/75656845/231967497-c0a3b821-3699-4b96-8f46-a2eca0d1a90c.png)

    
    - 모델링 알고리즘
        
    ![image](https://user-images.githubusercontent.com/75656845/231967571-e9d9e049-fcba-4296-9f15-85ab0a614901.png)
    
        
- 3-3. 산업 영역 구분
    
    도메인 리서치를 이용해 고려하여 산업을 3개의 영역으로 구분
    
    - 펫케어
    
    - 펫푸드
    
    - 펫용품
    
    참조: [글로벌 트렌드-펫산업이 뜬다] ①커지는 반려동물 시장...고급사료ㆍ털 미용 '펫팔자가 상팔자'
    
- 3-4. 영역 별  키워드 구분

: 키워드별 가중치로써 TF-IDF를 사용하였고, 토픽 분석을 위해 총 261개의 키워드를 추출하였다
   - 3-4-1. 뉴스 데이터 
   - 3-4-1-1. 전체 데이터 토픽 추출
       
     : 영역 별로 “2020-2022 반려동물 기사 중 가장 tf-idf값 높은 명사 200개”에서 가장 연관 높은 토픽 구분
        
        | 영역 | 키워드 | 영역 별 키워드 tf-idf 합계 |
        | --- | --- | --- |
        | 펫케어 | 진료비, 케어, 병원, 보험, 교육, 간식, 플랫, 테마파크, 영양제, 수의사 | 734.846775 |
        | 펫푸드 | 사료, 브랜드, 식품, 페어, 간식, 푸드, 친화, 영양제, 바이오, 강화 | 629.043142 |
        | 반려동물용품 | 용품, 브랜드, 이벤트, 보호, 가구, 제품, 관리, 플랫, 경상, 안전, 헬스 | 658.1310021 |
        
   - 3-4-1-2. 트랜드 분석(영역 별  tf-idf값 연도 별로 나눠서 트랜드 파악)
        
        ![image](https://user-images.githubusercontent.com/75656845/231969735-7f93d70c-7c9a-40c5-a898-9d06fb9737ed.png)
        
        - 도출 가능 사실:
            - **펫케어**가 가장 많은 관심도를 갖는 캐시카우 산업이지만 비중이 **감소**하고 있다.

   - 3-4-2. 특허 데이터
   - 3-4-2-1. 전체 데이터 토픽 추출
        
        영역 별로 “2020-2022 반려동물 기사 중 가장 tf-idf값 높은 명사 200개”에서 가장 연관 높은 토픽 구분
        
        | 영역 | 키워드 | 영역 별 키워드 tf-idf 합계 |
        | --- | --- | --- |
        | 펫케어 | 치료, 관리, 서비스, 예방, 진단 | 256.867341 |
        | 펫푸드 | 사료, 간식, 성분, 맞춤, 추출물 | 164.660985 |
        | 반려동물용품 | 장치, 조성물, 제조, 스마트, 패드 | 413.78245 |
        
   - 3-4-2-2. 트랜드 분석(영역 별  tf-idf값 연도 별로 나눠서 트랜드 파악)
        
        ![image](https://user-images.githubusercontent.com/75656845/231970521-cfb8c445-76f9-4b22-a710-79a48579ae87.png)
        
        - 도출 가능 사실:
            - **펫푸드**: 관심도가 조금씩 **감소**하고 있다. 즉 향후 성장도가 매우 **낮다.**
            - **반려동물용품**: 관심도가 빠르게 **증가**하고 있다. 즉 향후 성장도가 매우 **높다.**
    
- 3-5. 영역 별 주요 사업 선정
    - word2vec으로 분류된 3개의 영역 별 관련 사업 명칭
        
        **word2vec**을 이용하여 영역 별 관련 사업을 추출.
        
        - 모델링
            
            ```python
            from nltk.tokenize import word_tokenize, sent_tokenize
            from soynlp.tokenizer import RegexTokenizer
            from gensim.models import word2vec
            
            # RegexTokenizer 사용해 뉴스 기사 토크화
            tokenizer = RegexTokenizer()
            
            # 한글 데이터 전처리
            all_news_text = df_all_news["title"].str.replace("[^ㄱ-ㅎㅏ-ㅣ가-힣 ]","")
            %time tokens = all_news_text.apply(tokenizer.tokenize)
            
            # 로그를 출력하기 위해 불러오기
            import logging
            logging.basicConfig(
                format='%(asctime)s : %(levelname)s : %(message)s', 
                level=logging.INFO)
                 
            
            # 한국어 word2vec 모델에서 학습 알고리즘은 SG, 벡터 크기는 300, 윈도 크기는 5~10 사이가 최적이다. 
            # http://journal.dcs.or.kr/xml/19540/19540.pdf 기반으로 패러미터 튜닝
            
            model = Word2Vec(sentences = tokens, size = 300, window = 5,
             min_count = 5, workers = 4, sg = 1)
            
            #size = 워드 벡터의 특징 값. 즉, 임베딩 된 벡터의 차원.
            #window = 컨텍스트 윈도우 크기
            #min_count = 단어 최소 빈도 수 제한 (빈도가 적은 단어들은 학습하지 않는다.)
            #workers = 학습을 위한 프로세스 수
            #sg = 0은 CBOW, 1은 Skip-gram.
            ```
            
        
        영역 별 관련 사업 추출
            
        | 주제 | 주요 단어 | 주제 |
        | --- | --- | --- |
        | 펫케어 | [('스마트', 0.9995317459106445),  ('맞춤형', 0.9993774890899658),  ('제공하는', 0.9993467330932617),  ('프로그램', 0.9993445873260498),  ('펫', 0.9992979168891907),  ('동작', 0.9992449283599854),  ('플랫폼', 0.9992424249649048),  ('애완동물', 0.9991345405578613),  ('사용자', 0.9990638494491577),  ('인증', 0.9990534782409668)] | 맞춤형 스마트 펫 동작 및 사용자 인증 플랫폼 |
        | 펫푸드 | [('기능성', 0.9990904331207275),  ('제조된', 0.9986807703971863),  ('제조방법', 0.9986406564712524),  ('반려동물용', 0.9985523819923401),  ('이에', 0.9983112812042236),  ('의해', 0.9982779026031494),  ('첨가제', 0.9978259801864624),  ('따라', 0.9978204965591431),  ('간식', 0.9977717399597168),  ('고양이', 0.9977165460586548)] | 반려동물을 위한 기능성 첨가제 간식 |
        | 반려동물용품 | [('저장된', 0.999779999256134),  ('실시간', 0.9997744560241699),  ('놀이', 0.9997695088386536),  ('장치를', 0.9997622966766357),  ('확인', 0.9997620582580566),  ('통해', 0.9997577667236328),  ('기기', 0.9997555017471313),  ('인지', 0.999755322933197),  ('센서를', 0.9997507333755493),  ('기구', 0.9997498989105225)] | 인지 센서를 통한 실시간 놀이 장치 |
    

### 4. 결과물

- 4-1. **BCG** 매트릭스 기반 펫산업 분석
    
    ![image](https://user-images.githubusercontent.com/75656845/231970728-a3f26a72-24a8-408a-a270-80836f14527e.png)
    
    - **캐시카우 사업**(펫케어)
        
         : 뉴스 데이터를 봤을 떄 tf-idf 가 가장 높다. 즉 현재 가장 대중의 관심이 높은 영역이다.
        
    - **스타 사업** (반려동물용품)
        
         : 특허 데이터의 트렌드 분석을 통해 관심도가 빠르게 증가하고 있는 걸 알 수 있다. 즉, 향후 성장도가 매우 높다.
        
    - **도그 사업** (펫푸드)
        
         : 뉴스 데이터를 봤을 떄 tf-idf변화폭이 별로 없음을 알 수 있다. 또한 특허 데이터의 트렌드 분석을 통해 관심도가 조금씩 감소하고 있음을 알 수 있다. 즉 수익과 성장 가능성이 낮다. 
        
- 4-2. 2023년 반려동물 산업 **투자 전략**
    - 펫케어 스타트업 중 반려동물의 동작을 인증하는 맞춤형 스마트 펫 플랫폼에 투자하는 게 가장 안정적 투자를 할 수 있다.
    - 반려동물용품 스타트업 중 반려동물 인지 센서를 통한 실시간 놀이 장치 관련 사업이 빠르게 성장할 것으로 예상되므로 주의가 필요하다.
    - 예시 관련 제품
        
        ![image](https://user-images.githubusercontent.com/75656845/231971048-440740ea-8d59-4258-b1fc-984ddbf04718.png)
        
- 4-3. 데이터 분석 시각화 **Streamlit** 페이지
    
    [https://moksu27-pet-industry-prediction-streamlit-pet-industry-msl733.streamlit.app/](https://moksu27-pet-industry-prediction-streamlit-pet-industry-msl733.streamlit.app/)
    
- 4-4. 데이터 분석 설명 영상 (유튜브)
    
    [https://youtu.be/-HEeLbIue4w](https://youtu.be/-HEeLbIue4w)
    
- 4-5. 발표 ppt
    
    [https://www.canva.com/design/DAFWuJWkUpw/nrIX0yBORsl_MJfVscMALQ/view?utm_content=DAFWuJWkUpw&utm_campaign=share_your_design&utm_medium=link&utm_source=shareyourdesignpanel](https://www.canva.com/design/DAFWuJWkUpw/nrIX0yBORsl_MJfVscMALQ/view?utm_content=DAFWuJWkUpw&utm_campaign=share_your_design&utm_medium=link&utm_source=shareyourdesignpanel)
 

<br>

### 5. 프로젝트 회고 및 개선점

- 5-1. 현업자 피드백 + 각종 질문
    - 아쉬운 점
        - 오히려 tf-idf로 간단하게 분석한 것이 긍정적으로 다가왔지만 기술적으로 너무 쉬운 것만을 다뤄 아쉽다.
            - LDA와 같은 기술을 더 공부하여 적용하는 것을 추천
        - 데이터 분석 결과에 대해 이해는 하지만 근거를 좀 더 강화할 필요가 있음
        - 스트림릿 그래프에서 가독성이 떨어짐        
        - tf-idf가 어떻게 중요한지 및 한계점에 대해 설명해주면 더 좋았을 것 같다.
        - 톰슨샘플링(?), 확률론(?) 공부 하는 것도 추천
    - 잘한 점
        - tf-idf로 밀고 나간 논리의 흐름이 좋았다. 기승완결 완성도가 높다.
        - 리서치의 범위가 넓을 때 좁혀나가기 좋을 것 같다.
        - 특정 상황에서 해당 데이터를 유의미하게 잘 활용할 수 있을 것 같다.
    - 기대되는 결과
        - 반려동물 산업의 트렌드를 파악하여 관련 산업 관계자 및 투자자들에게 보다 시각적, 논리적으로 투자 아이템을 설득할 수 있습니다.
        - 반려동물 스타트업들의 시장 조사 및 제품 개선 방향을 도와줄 수 있습니다.
        - 기존 많은 시간과 비용 뿐 아니라 제한적으로만 가능했던 RA의 산업 관련 리서치를 DA의 도움을 받아 더 효율적이고 빠르게 수행할 수 있습니다.
        
- 5-2 개선점 (팀 내에서 논의 및 합의된 개선 방향)
    - LDA기술을 이용한 모델 재 구성및 기존 모델과의 비교 평가 진행
    - 토픽모델링을 최적화, 자동화할 수 있다면 반려동물 산업 뿐만 아니라 사용자가 원하는 모든 산업 관련 트랜드를 분석해주는 제네럴 모델을 배포할 수 있을 거라 생각합니다.
    - 펫산업 관련 도메인 지식을 지닌 전문가와 협의하여 보다 더 정확한 키워드 추출을 할 수 있습니다.
    - 스타트업 투자액이나 매출액을 분석하고 예상한 산업 및 사업 아이템 트렌드와 비교해본다면 분석의 설득력이 높아질 것이다.

<br>

### 6. 참고자료

- 기사 [커지는 반려동물 시장 고급자료 털미용 ‘ 펫팔자가 상팔자’](https://www.rndip.or.kr/opensvc/main.do?method=main)
 
- 논문 
[항공산업 미래유망분야 선정을 위한 텍스트 마이닝 기반의 트렌드 분석.pdf](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2c86c9b7-9d9b-4bc5-8674-2be16c125068/%ED%95%AD%EA%B3%B5%EC%82%B0%EC%97%85_%EB%AF%B8%EB%9E%98%EC%9C%A0%EB%A7%9D%EB%B6%84%EC%95%BC_%EC%84%A0%EC%A0%95%EC%9D%84_%EC%9C%84%ED%95%9C_%ED%85%8D%EC%8A%A4%ED%8A%B8_%EB%A7%88%EC%9D%B4%EB%8B%9D_%EA%B8%B0%EB%B0%98%EC%9D%98_%ED%8A%B8%EB%A0%8C%EB%93%9C_%EB%B6%84%EC%84%9D.pdf)
        
- 유튜브 [Analysing user comments with Doc2Vec and Machine Learning classification](https://www.youtube.com/watch?v=zFScws0mb7M&t=1150s)

- 유튜브 [자연어처리 2차 word2vec, fasttext와 doc2vec](https://www.youtube.com/watch?v=5ivVf-Guqk4&list=PLrLEKGJAgXxL-R9IqDH7HANWXRsS900tF&index=2)

- 리포트 [반려동물 전성시대, 관광시장에 나타난 펫 트렌드 분석](https://kto.visitkorea.or.kr/viewer/view.kto?id=71086&type=bd)

- 리포트 [2022년 소비 트렌드(반려동물에 소비하다)](https://www.mezzomedia.co.kr/data/insight_m_file/insight_m_file_1457.pdf)

- 리포트 [성장하는 펫케어 산업 최신트렌드와 우리 기업의 글로벌 경쟁력 강화 방안-포커스&브리프](https://www.kita.net/cmmrcInfo/internationalTradeStudies/researchReport/focusBriefDetail.do?pageIndex=1&no=2258&classification=5)
