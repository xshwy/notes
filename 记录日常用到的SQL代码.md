自定义排序
```sql
SELECT * FROM `SB_SCHEDULE`
WHERE RATE IS NOT NULL AND RATE!=''
ORDER BY SCHEDULE_DATE , FIELD(START_TIME,'8:00','18:30','21:00','21:30')
```

合并字段查询
```sql
SELECT CONCAT(field_a,'AAA',field_b) FROM SB_TASK  //field_a_valueAAAfield_b_value
```

查询结果补0
```sql
SELECT LPAD('AAA',6,0) // 000AAA
SELECT RPAD('AAA',6,0) // AAA000
```

查询结果包含
```sql
SELECT * FROM STUDENTS WHERE ID IN(1,2,3)
```
查询结果排除
```sql
SELECT * FROM STUDENTS WHERE NOT IN (1,2,3)
```
