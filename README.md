# pigjh1.github.com

`jekyll server`실행
http://localhost:4000/

- Voyager jekyll theme: http://redvi.github.io/voyager
- 커버용 이미지: https://pixabay.com/


```
index.hthml                     # index.html template
src/
├── main.js                     # app entry file
├── App.vue                     # main app component
├── components/                 # ui components
│   ├── StepButton.vue          # 이전, 다음, 결과 버튼
│   ├── StepField.vue           # 선택 필드
│   ├── StepInfo.vue            # step 상태바
│   └── StepRrsult.vue          # 측정 결과
└── store/
    ├── getters.js
    ├── index.js                # 모듈을 조합하고 저장소를 내보내는 곳
    ├── mutations.js
    ├── state.js
    └── state-result.js
```
