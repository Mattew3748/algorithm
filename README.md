## 참고 함수

### 배열
- **arr.splice(arr.index, x)** : 삭제할 arr.index부터 x개 삭제
- **isNaN(number)** : isNotNumber, 숫자일때 false return
- **parseInt(string)** : 숫자로 변환. ex) parseInt('0208') => 208
- **arr.sort([compareFuntion])** : 정렬 순서를 정의하는 함수.
    <pre>
    이 값이 생략되면, 배열의 element들은 문자열로 취급되어, 유니코드 값 순서대로 정렬됩니다.
    이 함수는 두 개의 배열 element를 파라미터로 입력 받습니다.
    이 함수가 a, b 두개의 element를 파라미터로 입력받을 경우,
    이 함수가 리턴하는 값이 0보다 작을 경우,  a가 b보다 앞에 오도록 정렬하고,
    이 함수가 리턴하는 값이 0보다 클 경우, b가 a보다 앞에 오도록 정렬합니다.
    만약 0을 리턴하면, a와 b의 순서를 변경하지 않습니다.
    ex) arr.sort( (a,b) => a - b)
    </pre>

### 숫자
- **Math.max()** : 최대값
- **Math.min()** : 최소값
- **Math.abs()** : 절대값
- **Math.sqrt()** : 제곱근




## 알고리즘

### 소수
- **루트 N 이하 수 나누기** : Math.sqrt() - 제곱근 함수
        입력 숫자 16

        1 * 16
        2 * 8
        4 * 4
        8 * 2
        16 * 1 

    둘중에 하나는 N에 루트를 씌운것보다 같거나 작다.
    즉 받은 숫자 N을 루트씌우고 그 이하의 숫자들로만 나눠보면 됨.
- **시간 복잡도** : 
                 해당숫자만 소수판별: O(√N)
                 숫자이하 소수구하기: O(N√N)


### 완전 탐색(brute force) - O(N^2)
- brute: 무식한, force: 힘   무식한 힘으로 해석할 수 있다.
- 완전탐색 알고리즘. 즉, 가능한 모든 경우의 수를 모두 탐색하면서 요구조건에 충족되는 결과만을 가져온다.
- 이 알고리즘의 강력한 점은 예외 없이 100%의 확률로 정답만을 출력한다.

- 알고리즘 설계의 가장 기본적인 접근 방법은 해가 존재할 것으로 예상되는 모든 영역을 전체 탐색하는 방법이다.
- 선형 구조를 전체적으로 탐색하는 순차 탐색, 비선형 구조를 전체적으로 탐색하는 깊이 우선 탐색(DFS, Depth First Search)과 너비 우선 탐색(BFS, breadth first search)이 가장 기본적인 도구이다.
* 너비 우선 탐색은 브루트 포스와 관련이 깊고, 깊이 우선 탐색은 다음에 작성될 백트래킹과 관련이 깊다
 

### Two Pointers 알고리즘 - O(N) 
 - start Point와 end Point로 두 개의 포인터를 사용합니다.
 - start는 부분배열의 앞 쪽을 가르키는 인덱스, end는 부분배열의 뒤 쪽을 가르키는 인덱스입니다.
 - 맨 처음에 두 포인터는 0에서 시작하며 항상 start<=end를 만족해야합니다.
 - 그리고 매 순간마다 부분합 배열의 합과 구해야하는 값을 비교하여 포인터를 이동하게 됩니다.
    - 부분합 배열의 합 < 구해야하는 값
    - end를 오른쪽으로 한 칸 이동하여 부분합 배열의 크기를 증가시킵니다.
    - 부분합 배열의 합 >= 구해야하는 값
    - start를 오른쪽으로 한 칸 이동하여 부분합 배열의 크기를 감소시킵니다.

### Sliding Window - O(N)
- 창문을 밀듯이 하나씩 옆으로 밀어 나가는 방식의 알고리즘이다.
- 투포인터 알고리즘은 end Point가 특정 조건에 만족될때까지 늘어난 후에 start Point가 늘어나는 방법인데 반해
  슬라이딩 윈도우 알고리즘은 창문 덩어리에서 end Point를 한칸 더해주고 start Point를 한칸 빼주는 방식으로 한칸씩이동하는 메커니즘이다.
   