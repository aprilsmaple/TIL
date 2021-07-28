# SWEA-D2-

## 2005. 파스칼의 삼각형

```python
T = int(input())

for t in range(T):
  # 몇 단 뽑을지 input
  stage = int(input())
  print('#{}'.format(t+1))

  answer = []
  
  for n in range(stage):
    # n번째줄 i번째항 담기 위한 이중 리스트
    mini = []
    for i in range(n+1):
   	  # 시작과 끝은 1
      if i == 0 or i == n:
        mini.append(1)
        # 함수 만들란 소리 없어서 그때 그때 print
        print(1, end=' ')
      else:
        # n 줄의 i = n-1 줄의 i-1 항과 i 항의 합
        value = answer[n-1][i-1] + answer[n-1][i] 
        mini.append(value)
        print(value, end=' ')
    print()
    answer.append(mini)
```

세부적으론 다르지만 (아직 내가 값을 넣기 전이니까 직전 줄을 [-1]로 뽑아낸 사람도 있었음 -근데 어차피 이것도 이중 for문-) 많이들 이차원 배열로 푼 듯 

## 2001. 파리 퇴치

```python
T = int(input())

for t in range(T):
  Ns, M = map(int, input().split())
  info = []
  # 이차원 배열 사용
  for n in range(Ns):
    info.append(list(map(int,input().split())))
  # 최댓값 변수 선언
  max = 0
  # 5중 for문
  # x, y는 시작점. 가장 작은 좌표 값
  # 가장 큰 index 값이 Ns-1이기에 x가 가질 수 있는 최댓값은 ns-1+M
  for x in range(Ns - M + 1):
    for y in range(Ns - M + 1):
      dead = 0
    # 한 번에 잡는 파리의 개수 더하기
    # 예) M = 2 면 (x,y) (x+1,y) (x, y+1) (x+1,y+1)의 합이니까 이거 다 더하기 
      for z in range(M):
        for u in range(M):
          dead += info[x+z][y+u]
      if dead > max:
        max = dead
  print('#{} {}'.format(t+1, max))

```

다들 이렇게 풀었다

## 1989. 초심자의 회문 검사 - 보류 -

```python
# replit이나 vs code 나 둘 다 맞게 나오는데 swea에서만 샘플 케이스도 오답으로 뜸 
# 회문은 이제 쉽지롱! 
T = int(input())

for t in range(T):
    word = input()
    answer = 1
    # len(word) 할 필요 없이 절반만 검사하면 끝. 길이가 홀수면 가운데는 검사할 필요도 없다. 
    for i in range(len(word)//2):
        if word[i] == word[-1 - i]:
            continue
        else:
            answer = 0
            break
    print('#{} {}'.format(t+1, answer))
```

## 1986. 지그재그 숫자

```python
T = int(input())

for t in range(T):
    N = int(input())
    total = 0

    for number in range(1, N+1):
        if number % 2:
            total += number
        else:
            total -= number
    print('#{} {}'.format(t+1, total))
```

## 1204. [S/W 문제해결 기본] 1일차 - 최빈수 구하기

```python
T = int(input())

for t in range(T):
    N = int(input())
    
    students = list(map(int,input().split()))
    # set로 만들어서 중복 제거. for문 돌리기 위해 다시 list로 변환
    scores = list(set(students))
    # 가장 많이 나온 게 몇 번인지 횟수
    max = 0
    # 가장 많이 count된 점수가 뭔지
    max_score = 0
    
    for score in scores:
        num = students.count(score)
        # 현재 max값보다 크다면 더 많이 나왔다는 뜻이니 max를 바꿔줌 
        if num > max:
            max = num
            max_score = score
    print('#{} {}'.format(N, max_score))
```

## 1954. 달팽이 숫자

```python
```



## enumerate

list의 인덱스 값을 같이 받아줌.

```python
names = ['홍길동', '길동', '동']
for idx, name in enumerate(names):
    print(idx, name) # 0 홍길동 1 길동 2 동
```

