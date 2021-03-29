# TextDifficultyAnalyzer

## 사용법
`word_analyzer.py` 를 import하여 `WordAnalyzer` class를 적절히 활용한다.  
`WordAnalyzer` class의 `analyzeText` 메소드를 활용하면 주어진 input text를 분석하여 json 형식으로 반환한다.

## 저장소 구조
- `word_analyzer.py` : 분석기 구현  
- `word_data` : 분석에 사용되는 데이터들  
- `analyze_result` : 분석 결과 예시  

## 분석 데이터
- CEFR 데이터 : 영단어의 수준을 CEFR 점수로 측정한 데이터
  * `oxford_5000_CEFR.csv` : 옥스포드에서 측정한 5000개 단어 리스트 / [출처](https://www.oxfordlearnersdictionaries.com/wordlists/oxford3000-5000)
  * `cefr_japanese.csv` : 일본인 대상 CEFR 단어 점수 리스트 / [출처](https://github.com/openlanguageprofiles/olp-en-cefrj)
- Dale Chall List : Dale Chall이 고안한 어렵지 않은 단어 목록 / [출처](https://readabilityformulas.com)
- 빈도수 데이터 : 자주 쓰이는 단어를 랭킹순으로 정렬(자주 쓰이면 친숙하다는 가정) / [출처](https://en.wiktionary.org/wiki/Wiktionary:Frequency_lists)
  * `tv_movie_script_10000.csv` : tv나 영화 대본에서 자주 쓰이는 단어 10000개 
  * `simpson_freq_5000.csv` : 에니메이션 심슨에서 자주 쓰이는 단어 5000개
  * `project_gutenberg_10000.csv` : 구텐버그 프로젝트에서 분석한 자주 스이는 단어 10000개
  
  
## 참고사항
- 문장 전체의 난이도는 사용된 단어의 CEFR 점수의 평균으로 구하였습니다.
- 빈도수를 CEFR 점수로 변환하는 것은 <http://polydog.org/index.php?threads/the-cefr-scale-and-language-level.26/> 를 참고하였습니다.
- 가독성 점수는 Dale Chall Readability Formula 를 사용하였습니다. <https://readabilityformulas.com/>
### CEFR 점수
- A1 A2 초급 및 중급 이전 수준
- B1 B2 중하급 및 중상급
- C1 고급수준
- C2 완전한 능숙도
### 가독성 점수
- 0.1579*어려운단어의 백분율 + 0.0496*(단어수/문장수)
- 4.9이하 : 4학년 수준
- 5.9이하 : 6학년 수준
- 6.9이하 : 8학년 수준
- ...
- 9.9이하 : 13에서 15학년(대학생) 수준
