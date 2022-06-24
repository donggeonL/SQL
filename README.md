# SQL

# NoSQL(몽고디비) RDBMS(mysql, maria 등등)
> NoSQL 은 일관성이 좋지않다 but 데이터를 찾아오는 포퍼먼스가 굉장히 좋다.</br>
> 몽고디비의 경우 비동기 통신이 가능한 데이터 베이스이다.</br>
>
> RDBMS 는 중복이 되지않고 데이터베이스 간의 공유와 변경이 용이하다.</br>
> 기존의 RDBMS는 비동기 통신을 지원하지 않는다, BUT R2DBC를 사용하면 비동기통신을 사용이 가능하다.</br>

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

> #### TABLE 생성하기
```sql
create table tb_eep_crprtn_card_m (                      ( 테이블 명 설정 )
CRPRTN_CARD_SQ bigint(21) not null primary key,          ( 칼럼 설정 SQ는 프라이머리키로 primary key 설정해주기 )
CRPRTN_CARD_BANK varcharacter(50) not null,
CRPRTN_CARD_NUM bigint(21) not null,
CRPRTN_CARD_USR_NM varcharacter(50) not null,
CRPRTN_CARD_USR_DEPT varcharacter(50) not null,
CRPRTN_CARD_USR_PST varcharacter(50) not null,
CRPRTN_CARD_USE_DT varcharacter(50) not null,
CRPRTN_CARD_CNT varcharacter(1000) not null,
CRPRTN_CARD_USE_PRC bigint(21) not null,
CRPRTN_CARD_NOTE varcharacter(1000) not null
);
```

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

> #### 기존 생성되어있는 칼럼에 Auto_Increment 설정하기
```sql
ALTER TABLE tb_eep_crprtn_card_m                        ( 테이블 명 )
MODIFY COLUMN CRPRTN_CARD_SQ  bigint auto_increment;    ( 칼럼 명 + Auto_Increment 테이블설계서를 보고 자료형 붙여주기 >> 때문에 int OR bigint 로 자료형 설정 )
```
