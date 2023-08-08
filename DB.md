# connection 이란?

DB에 쿼리를 날릴 수 있는 접속 단위 객체(?)

# pool이란

DB connection 개체들의 집합이다.

## 왜 pool을 사용하는가?

요청시 일일히 connection을 생성하는 것보단 미리 만들어 놓고 필요할 때마다 각 파일에서 connection을 불러다 쓰는 것이 경제적이기 때문이다.
