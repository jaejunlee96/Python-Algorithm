# 구현 (Implementation)

구현이란, __머릿속에 있는 알고리즘을 소스코드로 바꾸는 과정__

사실상 모든 알고리즘 문제들이 구현 문제이지만,

흔히 알고리즘 유형에서 구현이란, __풀이를 떠올리는 것은 쉽지만 소스코드로 옮기기 어려운 문제__를 지칭

구현 유형 예시
- 알고리즘은 간단한데 코드가 지나칠 만큼 길어지는 문제
- 실수 연산을 다루고, 특정 소수점 자리까지 출력해야 하는 문제
- 문자열을 특정한 기준에 따라서 끊어 처리해야 하는 문제
- 적절한 라이브러리를 찾아서 사용해야 하는 문제

##  시뮬레이션 및 완전 탐색 문제에서는 2차원 공간에서의 __방향 벡터__ 가 자유 활용됨
```python
# 동, 북, 서 ,남
dx = [0, -1, 0, 1]
dy = [1, 0, -1, 0]

# 현재 위치
x, y = 2, 2

for i in range(4):
  # 다음 위치
  nx = x + dx[i]
  ny = v + dy[i]
  print(nx, ny)
```

----

### 예시 문제 : 상하좌우

- 여행가 A 는 N x N 크기의 정사각형 공간 위에 서 있다. 이 공간은 1x1 크기의 정사각형으로 나누어져 있다. 가장 왼쪽 위 좌표는 (1,1) 이며, 가장 오른쪽 아래 좌표는 (N,N)에 해당한다. 여행가 A 는 상, 하, 좌, 우 방향으로 이동할 수 있으며, 시작 좌표는 항상 (1,1) 이다. 우리 앞에는 여행가 A가 이동할 계획이 적힌 계획서가 있다.
- 계획서에는 하나의 줄에 띄어쓰기를 기준으로 하여 L, R, U, D 중 하나의 문자가 반복적으로 적혀있다.
  - L : 왼쪽으로 한 칸 이동
  - R : 오른쪽쪽으로 한 칸 이동
  - U : 위로 한 칸 이동
  - P : 아래로 한 칸 이동

- 이때, 여행가 A 가 N x N 크기의 정사각형 공간을 벗어나는 움직임은 무시됨


- 입력 조건
  - 첫째 줄에 공간의 크기를 나타내는 N 이 주어진다. (1<=N<=100)
  - 둘째 줄에 여행가 A 가 이동할 계획서 내용이 주어진다.  (1<= 이동 횟수 <=100)
- 출력 조건
  - 첫째 줄에 여행가 A가 최종적으로 도착할 지점의 좌표 (X,Y)를 공백을 기준으로 구분하여 출력한다.

- 입력 예시
```
5
R R R U D D
```

- 출력 예시
```
3 4
```
----
### 문제 풀이
```python
n = int(input())
plans = input().split()

# 현재 좌표
x, y = 1, 1

# L, R, U, D
dx = [0, 0, -1, 1]
dy = [-1, 1, 0, 0]
move_types = ['L', 'R', 'U', 'D']

# 이동 계획을 하나씩 확인하기
for plan in plans:
    for i in range(len(move_types)):
        if plan == move_types[i]:
            nx = x + dx[i]
            ny = y + dy[i]
    
    # 공간을 벗어나는 경우 무시
    if nx < 1 or ny < 1 or nx > n or ny > n:
        continue
    
    # 이동 수행
    x, y = nx, ny

print(x, y)
```