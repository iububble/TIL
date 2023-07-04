# git이란?

git이란 **분산** 버전관리프로그램이다.

# 버전관리란?

변경사항에 관한 일시, 작업자, 변경내용등을 저장하는 것<br>
=> 즉 코드의 이력(history)를 관리

# git의 특징

**분산** 버전관리<br>
내 컴퓨터 뿐만 아니라 원격 컴퓨터도 버전관리가 가능하다.

```
 아직은 뭔소린지 모르겠다
```

## Why 왜 배울까?

### 1. 쉽게 이전 상태로 되돌리기 위해

### 2. 타인과의 협업이 용이하게

> git을 통해 타인의 코드를 보고 편집을 할 수 있다.

# git 사용 과정

### git add [파일명]

해당 파일 git 관리 위해 등록

### git commit -m "[메시지]"

add된 파일=tracked file을 로컬 저장소(내 컴퓨터)에 저장

### git push [원격 저장소명]

로컬 저장소의 파일(commit된 파일)을 원격저장소에 저장

### .gitignore (점gitignore)

.gitignore 내부에 작성된 파일명의 파일은 git으로 관리되지 않는다.<br>
=> 비밀번호, 보안, 로그 파일 등 공유하면 안되는 파일을 작성

# git log

commit한 기록을 확인할 수 있다.<br>
=이력관리(history management)

```
git log --stat
# 각 커밋별 세부내용(추가/삭제)를 볼 수 있다.
# enter로 넘어가고 q로 빠져나올 수 있다.
```

# git checkout [해시값]

해시값=git log에서 보이는 commit의 고유한 <br>
해당 커밋의 상태로 돌아간다.<br>

**주의** <br>
이 경우 git log 화면도 이전으로 돌아간다.<br>
따라서 뒤로 다시 원래대로 하려면 원래 commit의 해시값 잘 찾아야 한다.

git checkout 활용사례 : https://zoosso.tistory.com/729
