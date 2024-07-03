# 육아지원정책: KoBERTopic과 SNA를 통한 심층 분석 


## 데이터셋: 
> 네이버 맘카페 '맘스홀릭베이베' 개시글 제목과 내용 크롤링 (약 4000개의 텍스트 데이터)

​

## Research Question: 

> 정권교체와 시기에 따른 육아지원 정책들이 꾸준하게 신규 수립되고 수정되고 있다. 그렇다면 정작 바뀌는 정책에 따라 부모들은 이러한 정보를 정확하게 인지 하고 있을까?

</br>
</br>

## 연구 배경:

> 직장을 병행하는 부모의 입장에서 꾸준한 정보의 생성은 정보의 비대칭을 야기할 것으로 판단한다. 많은 육아지원정책이 존재하지만 워라밸을 중시하는 현재 시기에서 육아휴직에 대한 토픽은 끊이지 않고 있다. 3+3 육아휴직제도, 아빠 육아휴직 장려금 등 매년 새로운 육아휴직에 관한 제도가 새롭게 제정되고 있다. "이렇게 매번 변하고 어려운 육아지원정책에 대한 정보를 더 쉽고 명확하게 전달할 수 있는 방법을 마련해보자"가 이번 연구의 배경이자 타겟이다.

​

## Reference:
1. 텍스트마이닝 방법을 이용한 간편결제 서비스 이용자의 질문분석
> 위 논문에서는 텍스트마이닝을 이용해 소비자들이 간편결제서비스를 이용하면서 가장 많이 묻는 질문을 분석했으며, 그 질문에 한해 관심도를 파악했다. 하지만 본 연구는 문서 별로 자주 나온 단어를 clustering 하여 질문을 재구성하는데 초점을 맞추었다.

​

2. 소셜 네트워크 분석을 통한 국민의 관광에 대한 인식 변화 연구
> 관광에 대한 인식을 파악하고자 빈도수가 잦은 단어를 하나의 클러스터로 묶어 해석을 용이하게 했다. 따라서 본 연구에서도 해당 논문의 방법론을 벤치마킹하여 단어들 사이의 연관성을 파악하기 위해서 클러스터링을 진행했다.

​

3. AI 챗봇을 활용한 정부 및 지자체의 해택, 복지, 소식 정보 제공 및 추천 서비스에 대한 연구 
> 위 논문에서는 다양한 플랫폼을 활용해 정보 및 지자체 혜택 및 정보 추천 서비스를 제공하는 챗봇을 구현했다. 이 논문을 바탕으로 빈도수 기반의 재구성된 질문을 사전에 역제시하면서 효율적으로 정보를 제공하는 아이디어를 얻었다.

​

## 방법론:
1. TF-IDF

> 정보검색과 텍스트마이닝에서 이용하는 가중치, 어떤 단어가 특정문서에서 얼마나 중요한지를 나타내는 통계적 수치이다.
> 모든 문서에서 자주 등장하는 단어는 중요도가 낮다고 판단하며, 특정 문서에만 자주 등장하는 단어는 중요도가 높다고 판단한다. 다시말해, TF-IDF 값이 낮으면 중요도가 낮은 것이며 반대로 크면 중요도가 큰 것이다.
>> 즉, 문장에서는 많이 나오는데, 문서 전체에서는 적게 나오는 단어를 중요도가 높다고 판단한다.
> 본 연구에서는 '육아휴직', '기간' 등과 같은 단어의 경우에는 모든 문서에 자주 등장하기 때문에 자연스럽게 TF-IDF의 값이 다른 단어에 비해서 낮아지게 된다.



2. Social Network Analysis

> 사회적 관계망을 분석하는 기술로, 개인 또는 조직 사이의 관계와 상호작용을 시각화하여 분석하는 방법이다.
> 이때 Node는 질문에서 토픽이 되어 자주 등장하는 단어들이 될 것이며, Weight은 각 단어들이 게시글 내에서 동시 출현하는 빈도가 될 것이다.

​
3. Community Detection

> Louvain algorithm을 사용하며, 네트워크 내에서 밀도가 높은 커뮤니티를 식별하고 구조를 파악하여 서로 묶어서 분석하는 방법이다. 

