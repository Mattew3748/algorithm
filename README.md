## 참고 함수

### 배열
- **arr.splice(arr.index, x)** : 삭제할 arr.index부터 x개 삭제
- **arr.pop()** : 배열의 마지막 요소 삭제
- **arr.shift()** : 배열의 첫번째 요소 삭제
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
    ! 값은 a가 b 뒤라고 생각하면 편하다
    ex) const arr = [2,1,3,10] -> arr.sort( (a,b)=> {return a - b } ) -> arr.sort( (1,2) { retunr 1-2 } ) -> -1 -> [1,2,3,10] 
    ex) 2차배열 2번째 값 정렬 후 1번째 값 정렬
       - let arr=[[1, 4], [2, 3], [1, 3], [4, 6], [5, 7]]; 
            => meeting.sort( (a,b) => {
                                        if(a[1] < b[1]) return -1;
                                        if(a[0] < b[0]) return -1;
                                    }) 
            => [[1, 3],[2, 3],[1, 4],[4, 6],[5, 7]]
    </pre>
- **Array.from(iter, (val,index) => index +1 )** ; 문자열 등 유사 배열(Array-like) 객체나 이터러블한 객체를 배열로 만들어주는 메서드입니다. 

### 숫자
- **Math.max()** : 최대값
- **Math.min()** : 최소값
- **Math.abs()** : 절대값
- **Math.sqrt()** : 제곱근

### Map
 - **new Map()** : 맵을 만듭니다.
 - **map.set(key, value)** : key를 이용해 value를 저장합니다.
 - **map.get(key)** : key에 해당하는 값을 반환합니다. key가 존재하지 않으면 undefined를 반환합니다.
 - **map.has(key)** : key가 존재하면 true, 존재하지 않으면 false를 반환합니다.
 - **map.delete(key)** : key에 해당하는 값을 삭제합니다.
 - **map.clear()** : 맵 안의 모든 요소를 제거합니다.
 - **map.size** : 요소의 개수를 반환합니다.




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

### 스택(Stack) - LIFO - O(N)
- 스택은 들어온 순서의 반대 순서대로 나가고 LIFO 형식의 자료구조이다.
-  a -> b -> c 순서대로 들어간 입력을 역순으로 a -> b -> c 순서대로 출력해주게 됩니다. 

### 큐(Queue) - FIFO - O(N)
- 큐는 들어오는 순서대로 나가고 FIFO 형식의 자료구조이다.
- a -> b -> c 순서대로 들어간 입력을 그대로 c -> b -> a 순서대로 출력해주게 됩니다.

### 선택정렬 - O(N^2)
- Selection Sort는 Bubble Sort과 유사한 알고리즘으로, 해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 알고리즘이다.
- Selection Sort와 Insertion Sort를 헷갈려하는 사람들이 종종 있는데, Selection Sort는 배열에서 해당 자리를 선택하고 그 자리에 오는 값을 찾는 것이라고 생각하면 편하다.

### 버블정렬 - O(N^2)
- Bubble Sort는 Selection Sort와 유사한 알고리즘으로 서로 인접한 두 원소의 대소를 비교하고, 조건에 맞지 않다면 자리를 교환하며 정렬하는 알고리즘 이다.(끝자리부터 채우는 방식)
- 이름의 유래로는 정렬 과정에서 원소의 이동이 거품이 수면으로 올라오는 듯한 모습을 보이기 때문에 지어졌다고 한다.
- for문안에 for문의 j,j+1을 비교하여 스왑.

### 삽입정렬 - O(N^2)
- 두 번째 원소부터 시작하여 그 앞의 원소들과 비교하여 삽입할 위치를 지정한 후, 원소를 뒤로 옮기고 지정된 자리에 자료를 삽입하여 정렬하는 알고리즘이다.
- 첫번째 for문은 배열은 tmp 로 저장하고 j를 변수선언한다.
- 첫번째 for는 1부터 시작하고, 두번째 for문은 i-1 부터 감소하면서 위치를 바꿔준다. 
- 두번째 for문이 끝난 후, j+1 을 tmp 값을 저장한다 .

### 이분검색 - O(logN)
- 이분탐색이란, 정렬된 배열에서 특정 값을 찾는 탐색 알고리즘이다. 
- 배열의 중간을 기준으로 데이터를 탐색하기 때문에 반드시 데이터가 정렬된 상태로 존재해야 한다.
- 이진 탐색의 시간 복잡도는 O(logN)으로 배열을 전수 조사하는 O(N)에 비하면 상대적으로 빠른 탐색 알고리즘에 속한다.
-  O(logN)만에 값을 찾을 수 있는 이유는 중간을 기준으로 탐색 대상을 절반씩 줄여나가기 때문이다.
- 중간값 === 타켓값 : 정답 / 중간값 < 타켓값 : lt = mid+1 / 중간값 > 타켓값 : rt = mid-1 / 중간값 : parseInt((lt+rt)/2)

