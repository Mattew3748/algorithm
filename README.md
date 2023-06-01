## 참고 함수

### 배열
- **arr.splice(arr.index, x)** : 삭제할 arr.index부터 x개 삭제
- **isNaN(number)** : isNotNumber, 숫자일때 false return
- **parseInt(string)** : 숫자로 변환. ex) parseInt('0208') => 208

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


