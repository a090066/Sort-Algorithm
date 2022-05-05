# **Sort-Algorithm Analysis**

- 이번에는 **정렬 알고리즘**에 대해서 분석해보려고 한다. 
- 다양한 정렬 알고리즘이 있지만 보편적으로 많이 알려져있는 **버블 정렬, 선택 정렬, 삽입 정렬, 쉘 정렬, 힙 정렬, 퀵 정렬**에 대한 기억이 가물가물해 다시 개념을 간단히 정리한 뒤, 분석을 진행할 예정이다.
- 분석은 정렬 별로 **시간 복잡도(소요시간)** 를 각 정렬별 그래프로 나타내 한 눈에 보기 쉽게 나타내보려 한다. 보통 **시간복잡도**는 최악의 경우로 나타내지만, 깊이 들어가보면 3가지 종류로 나눠볼 수 있다. 바로 **최선의 경우, 평균, 최악의 경우** <br/>
   - 그래프로 나타낼 때, 다음 3가지 기준에 따라 다르게 표시한다.<br/>
   ① 이미 정렬이 되어있는 경우(최선의 경우) <br/>
   ② 랜덤으로 정렬되어 있는 경우(평균)<br/>
   ③ 역순으로 정렬 되어있는 경우(최악의 경우)
- **input data값**은 2<sup>5</sup>(= 32)부터 1제곱씩 늘려가며 2<sup>6</sup>, 2<sup>7</sup>, ∙∙∙, 2<sup>20(</sup>(1048576)까지 범위를 제한해두고 input data값의 크기에 따라 정렬되는데 걸리는 소요시간을 그래프로 나타내보고자 한다. 2<sup>5</sup>부터 2<sup>20</sup>의 값은 다음과 같다.
<br/>

|Num|2<sup>n</sup>에서 n|결과값|
|:---|:-----:|:------:|
|1|5|32|
|2|6|64|
|3|7|128|
|4|8|256|
|5|9|512|
|6|10|1024|
|7|11|2048|
|8|12|4096|
|9|13|8192|
|10|14|16384|
|11|15|32768|
|12|16|65536|
|13|17|131072|
|14|18|262144|
|15|19|524288|
|16|20|1048576|

<br/>

- 이 수들을 배열의 input값으로 넣었을 때 각 정렬이 소요되는 시간을 알아보자.

- 추가로 각 정렬별로 등장하는 소요시간 값에 log<sub>2</sub>을 취했을 때 그래프 상에서 어떠한 변화가 나타나는지도 같이 나타내보고자 했다.

- 그러나, 



___
## Reference
- **'알기 쉬운 알고리즘'** - *양성봉* 著
- **'C언어로 쉽게 풀어쓴 자료구조'** - *천인국 外 2* 著