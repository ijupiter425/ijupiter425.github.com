# DB

source: `{{ page.path }}`

 __시간 정보 변환__
 ```sql
select unix_timestamp( '2019-05-16 15:50:00' );
select from_unixtime( 1557989400 );
```
 __날짜 변환__
 ```sql
select day, sum(item_amt)
from
    ( SELECT date_format(log_date, '%Y:%c:%d') as day, item_amt FROM payment_log ) T
group by day
order by day desc;

MSSQL => CONVERT(varchar(30), log_date, 102)
```

__데이터 추가시 인덱스 제거__
 ```sql
ALTER TABLE 테이블 DISABLE KEYS;
Insert 구문 수행
ALTER TABLE 테이블 ENABLE KEYS;
```

__update join__
 ```sql
UPDATE achievement_hero_record AS A JOIN 
(
        SELECT * FROM ", i_MergeDB_1 , ".achievement_hero_record AS T1 JOIN excel_info._vn_tw_achievement_task_type_diff_info AS T2
        ON T1.task_type = T2.vn WHERE T2.tw > 0 
) AS B
ON A.player_id = B.player_id AND A.task_type = B.task_type
SET A.task_type = B.tw;
```

__delete join__
 ```sql
delete X from item as X
inner join 
(
        select reward_item_id
        from mail
        where id between 6638251121050624000 and 6638447414477824000 and content = '{"langCode":47}' and title = '{"langCode":47}'
) as Y
on( X.id = Y.reward_item_id );
```

__column name__
 ```sql
select COLUMN_NAME
from INFORMATION_SCHEMA.columns
where table_schema='ps_ws_game_tw'
and table_name='auction_house_item'
```

__row count 구하기__
```sql
SELECT
table_name,
table_rows
FROM
information_schema. tables
WHERE table_schema = 'lin2ws_game1431' and information_schema. tables.table_name = 'item';
```

__lock 정보 조회__
```sql
select * from information_schema.INNODB_LOCK_WAITS;
select * from information_schema.INNODB_LOCKS;
select * from information_schema.INNODB_TRX;
select @@innodb_lock_wait_timeout;
select * from information_schema.innodb_trx;
show engine innodb status
```

__schema 추출__
```sql
 mysqldump --routines -h 183.110.84.19 -P 58306 -u west_srv -p ps_ws_game_j > database_schema.sql
```

__chracter set 변경__
```sql
alter table 테이블명 convert to character set utf8;
```

__insert join__
```sql
insert into achievement_erika_record value
select X.player_id, 20, 352, 3, 1
from
        (
                SELECT * FROM season_character_active
                where season_character_stage >= 3
        ) as X 
        left join 
        (
                SELECT player_id FROM achievement_erika_record
                where type = 20 and task_type = 352 
        ) as Y
    on( X.player_id = Y.player_id )
where Y.player_id is null;
```

__csv to DB__
```sql
"CREATE TABLE temp_data
(
                server_id int
        ,        server_name nvarchar(64)
        ,        player_id bigint
        ,        info_id   int
        ,   data1     tinyint
        ,   data2     tinyint
) engine=innodb;

LOAD DATA INFILE 'F:/perforce/l2/Branches/TW/Dev/Server/Tools/QueryToExcel/Asia/Result.csv' INTO TABLE temp_data FIELDS TERMINATED BY ',';"
```

__테이블 복사( index 포함 )__
```sql
create table belt_stud_book_20211102 like belt_stud_book;
```

__event__
```sql
CREATE EVENT IF NOT EXISTS [이벤트 이름]
    ON SCHEDULE
       AT '2018-11-02 13:40:13' -- 특정 시간에 1회 실행
    ON COMPLETION NOT PRESERVE
    ENABLE
    COMMENT [코멘트]
    DO 
    [수행할 명령]
END

drop event 이벤트 이름
select * from information_schema.events;
show variables like 'event%';
```
