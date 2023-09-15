# h1 [![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FDDak-Dae&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)            
<p align="center">
  <img src="https://github.com/DDak-Dae/.github/assets/99469068/c4f4e8cb-7103-446f-9f66-78ac598b077d">
</p>
<p align="center">
   1시간 걸리는 작업을 1분 만에 끝낼 수 있도록 도와주는 웹 서비스
</p>


<!-- ![Alt text](./images/image-3.png) -->
<p align="center">
<img width="668" alt="image-3" src="https://github.com/DDak-Dae/.github/assets/99469068/abbe3c12-a16c-4cf9-87ca-3910a20ae6a2">
</p>


<p align="center">
    서비스 소개 영상 : https://youtu.be/6h0SfTX4uwk
</p>

## 팀원
<p align="center">
  <img width="690" alt="image-1" src="https://github.com/DDak-Dae/.github/assets/99469068/6b6d35e7-ea6a-4dd5-981d-c676c93f7e41">
  
</p>



## 문제 및 개선
### 데이터 저장 방식

  <p align="center">
    <img width="556" alt="image-5" src="https://github.com/DDak-Dae/.github/assets/99469068/352d1a9b-1db2-484f-9904-9deaaf967982">
</p>
DB에서 검색 속도 향상을 위해 Chroma DB를 사용하였습니다.  
사용자가 저장한 파일들은 임베딩 되어 벡터값으로 DB에 저장됩니다.  


  <p align="center">
    <img width="566" alt="image-6" src="https://github.com/DDak-Dae/.github/assets/99469068/5084d207-6db9-449a-9928-821ccde94bac">
</p>
기존 MySql에서 검색하였을 때보다 약 7배 향상된 검색 성능을 보였습니다.

### 검색어 변환

  <p align="center">
    <img width="553" alt="image-8" src="https://github.com/DDak-Dae/.github/assets/99469068/a4c06449-097e-458f-8f64-a13f61a5f2b1">
</p>
처음 기획은 자연어를 학습 된 GPT를 통해 Qurey 명령어로 변환하려고 하였습니다.  
비용 문제와 데이터베이스 종류 교체로 검색어 변환 방식을 교체했습니다.  
사용자의 질의를 Open AI를 사용하여 Query 벡터로 교환하였습니다. 

### 토큰 제한

  <p align="center">
    
<img width="296" alt="image-10" src="https://github.com/DDak-Dae/.github/assets/99469068/2084bb61-848a-47bf-9146-635f915a3674">
</p>
토큰 제한으로 인해 대용량의 파일을 모두 GPT에게 보내는 것은 불가능 했습니다.  

  <p align="center">
    <img width="606" alt="image-11" src="https://github.com/DDak-Dae/.github/assets/99469068/ba7ed23e-566b-4c5d-ae9e-2252846af28d">
</p>
![Alt text](image-11.png)
이를 해결하기 위해 모든 파일을 토큰 단위로 쪼개어 저장하였습니다.  
초기에는 500 토큰 단위로 분할하였으나 응답이 부정확하였습니다.  
여러 실험 끝에 가장 정확한 응답을 생성하는 1000 토큰 단위로 수정하였습니다.  

  <p align="center">
    <img width="289" alt="image-13" src="https://github.com/DDak-Dae/.github/assets/99469068/bbb49ef7-cfb7-429c-b9cc-ebd8468c7c55">
</p>
Query 벡터와 유사한 상위 4개의 벡터를 Vector DB에서 추출하여 GPT에게 전송함으로써 토큰 제한 문제를 해결했습니다.

## 아키텍쳐

  <p align="center">
    <img width="474" alt="image-14" src="https://github.com/DDak-Dae/.github/assets/99469068/6857195c-253c-4030-83e8-9cac2e0c3fbf">
</p>



<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
