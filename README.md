# 발견 문제

# 1.시작시 에러 발생

> **원인** :
WriteDAO에서WriteDTO의 정보를 찾아와야는데 패키지 위치가 잘 못 되어 있어 찾아오질 못 하고 있었다 그래서 domain을 추가 하여 해결

```java
resultType="com.lec.spring.WriteDTO" ==> resultType="com.lec.spring.domain.WriteDTO"
```


# 2.업데이트 이후updateOk.jsp 에러 발생

> **원인** :
수정 완료 후 update된 parameter 값이 출력 되야하는데 안되고 있어 확인 결과 param값을 안넘겨주고 있어 아래와 같이 수정함 

```java
location.href = "view.do?uid=${uid}"; ==> location.href = "view.do?uid=${param.uid}";
```


# 3.해당글 삭제시 500에러

> **원인** :
WriteDAO 글 삭제 부분에 해당 부분 확인 결과 DB에 있는 wr_uid를 보내줘야 하는데 uid로 잘 못 된 정보가 전달되고 있었음 그리하여 아래와 같이 수정함


```java
DELETE FROM test_write WHERE uid = #{uid} ==> DELETE FROM test_write WHERE wr_uid = #{uid}
```