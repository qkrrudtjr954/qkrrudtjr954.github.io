# jsp 제일 처음에 생기는 에러


jsp파일 제일 첫번째 라인에 컴파일에러가 뜨는에러.

실행해보면 이상없이 실행되긴하지만 뭔가 문제가 있어보이는에러.



해결법은

프로젝트 우클릭 -> Build Path -> Configure Build Path…-> Libraries 탭 -> add library

-> server runtime -> was 선택 -> 끝
