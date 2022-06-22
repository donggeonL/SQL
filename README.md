# SQL

## 몽고DB
> #### DB 목록 확인
> show dbs;

> #### DB 스위칭
> use (db이름);

> #### DB 내용 보기
> db.db(이름).find();


## MYSQL (MariaDB)

> #### 동적 쿼리
> EMPLY_SQ = ${ EMPLY_SQ } ( 이런식으로 작성 )

> #### SELECT 사용법
```sql
select              (칼럼명)
`EMPLY_ACCT`,
`EMPLY_BNK`,
`EMPLY_ID`
from tb_eep_emply_m (테이블 명)
```

> #### INSERT 사용법
```sql
insert into tb_eep_emply_m (`EMPLY_ACCT`, `EMPLY_BNK`, `EMPLY_ID`)
             테이블 명        칼럼명         칼럼명       칼럼명
values('302-3092-0433-81', '농협', 'leedong')
             value          value     value
```

> #### UPDATE 사용법
```sql
update tb_eep_emply_m   (테이블 명)
set
EMPLY_BNK = '기업' ,                  (칼럼명 = 변경값)
EMPLY_ACCT = '1002-979-001543-12'     (칼럼명 = 변경값)
where EMPLY_SQ = 202                  WHERE (PRIMARY KEY) = (변경할 키 값)
```

> #### DELETE 사용법
```sql
delete from
tb_eep_emply_m  ( 테이블 명 )
where
EMPLY_SQ = 202  ( 지울 값 PRIMARY KEY )
```

> #### LIKE CONCAT 사용법 검색기능으로 많이 사용한다.
```sql
select 
`EMPLY_SQ` ,                (칼럼명)
`EMPLY_BNK` ,               (칼럼명)
`EMPLY_ACCT`,               (칼럼명)
`EMPLY_NM`                  (칼럼명)
from tb_eep_emply_m         (DB명)
where `EMPLY_NM`            (검색할 칼럼 명)
LIKE CONCAT('%', '김김김' , '%')         (MYSQL에서의 방식 >>> 동적쿼리 사용 할 시 >>> EMPLY_NM LIKE CONCAT('%', #{KEYWORD}, '%') )
```
