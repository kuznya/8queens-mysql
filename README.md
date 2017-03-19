# math-8queens-mysql
8 queens issue solution on MySQL

[SQL Fiddle][1]

**MySQL 5.6 Schema Setup**:

    CREATE TABLE `t` (`i` INT AUTO_INCREMENT, PRIMARY KEY(`i`));
    INSERT INTO t (i) VALUES(1),(2),(3),(4),(5),(6),(7),(8);
**Query 1**:

    select
        t1.i as i1,
        t2.i as i2,
        t3.i as i3,
        t4.i as i4,
        t5.i as i5,
        t6.i as i6,
        t7.i as i7,
        t8.i as i8
    from t t1
    inner join t t2
    on t2.i not in (t1.i,t1.i-1,t1.i+1)
    inner join t t3
    on t3.i not in (t1.i,t2.i,t2.i-1,t2.i+1,t1.i-2,t1.i+2)
    inner join t t4
    on t4.i not in (t1.i,t2.i,t3.i,t3.i-1,t3.i+1,t2.i-2,t2.i+2,t1.i-3,t1.i+3)
    inner join t t5
    on t5.i not in (t1.i,t2.i,t3.i,t4.i,t4.i-1,t4.i+1,t3.i-2,t3.i+2,t2.i-3,t2.i+3,t1.i-4,t1.i+4)
    inner join t t6
    on t6.i not in (t1.i,t2.i,t3.i,t4.i,t5.i,t5.i-1,t5.i+1,t4.i-2,t4.i+2,t3.i-3,t3.i+3,t2.i-4,t2.i+4,t1.i-5,t1.i+5)
    inner join t t7
    on t7.i not in (t1.i,t2.i,t3.i,t4.i,t5.i,t6.i,t6.i-1,t6.i+1,t5.i-2,t5.i+2,t4.i-3,t4.i+3,t3.i-4,t3.i+4,t2.i-5,t2.i+5,t1.i-6,t1.i+6)
    inner join t t8
    on t8.i not in (t1.i,t2.i,t3.i,t4.i,t5.i,t6.i,t7.i,t7.i-1,t7.i+1,t6.i-2,t6.i+2,t5.i-3,t5.i+3,t4.i-4,t4.i+4,t3.i-5,t3.i+5,t2.i-6,t2.i+6,t1.i-7,t1.i+7)

**[Results][2]**:

| i | i | i | i | i | i | i | i |
|---|---|---|---|---|---|---|---|
| 1 | 5 | 8 | 6 | 3 | 7 | 2 | 4 |
| 1 | 6 | 8 | 3 | 7 | 4 | 2 | 5 |
| 1 | 7 | 4 | 6 | 8 | 2 | 5 | 3 |
| 1 | 7 | 5 | 8 | 2 | 4 | 6 | 3 |
| 2 | 4 | 6 | 8 | 3 | 1 | 7 | 5 |
| 2 | 5 | 7 | 1 | 3 | 8 | 6 | 4 |
| 2 | 5 | 7 | 4 | 1 | 8 | 6 | 3 |
| 2 | 6 | 1 | 7 | 4 | 8 | 3 | 5 |
| 2 | 6 | 8 | 3 | 1 | 4 | 7 | 5 |
| 2 | 7 | 3 | 6 | 8 | 5 | 1 | 4 |
| 2 | 7 | 5 | 8 | 1 | 4 | 6 | 3 |
| 2 | 8 | 6 | 1 | 3 | 5 | 7 | 4 |
| 3 | 1 | 7 | 5 | 8 | 2 | 4 | 6 |
| 3 | 5 | 2 | 8 | 1 | 7 | 4 | 6 |
| 3 | 5 | 2 | 8 | 6 | 4 | 7 | 1 |
| 3 | 5 | 7 | 1 | 4 | 2 | 8 | 6 |
| 3 | 5 | 8 | 4 | 1 | 7 | 2 | 6 |
| 3 | 6 | 2 | 5 | 8 | 1 | 7 | 4 |
| 3 | 6 | 2 | 7 | 1 | 4 | 8 | 5 |
| 3 | 6 | 2 | 7 | 5 | 1 | 8 | 4 |
| 3 | 6 | 4 | 1 | 8 | 5 | 7 | 2 |
| 3 | 6 | 4 | 2 | 8 | 5 | 7 | 1 |
| 3 | 6 | 8 | 1 | 4 | 7 | 5 | 2 |
| 3 | 6 | 8 | 1 | 5 | 7 | 2 | 4 |
| 3 | 6 | 8 | 2 | 4 | 1 | 7 | 5 |
| 3 | 7 | 2 | 8 | 5 | 1 | 4 | 6 |
| 3 | 7 | 2 | 8 | 6 | 4 | 1 | 5 |
| 3 | 8 | 4 | 7 | 1 | 6 | 2 | 5 |
| 4 | 1 | 5 | 8 | 2 | 7 | 3 | 6 |
| 4 | 1 | 5 | 8 | 6 | 3 | 7 | 2 |
| 4 | 2 | 5 | 8 | 6 | 1 | 3 | 7 |
| 4 | 2 | 7 | 3 | 6 | 8 | 1 | 5 |
| 4 | 2 | 7 | 3 | 6 | 8 | 5 | 1 |
| 4 | 2 | 7 | 5 | 1 | 8 | 6 | 3 |
| 4 | 2 | 8 | 5 | 7 | 1 | 3 | 6 |
| 4 | 2 | 8 | 6 | 1 | 3 | 5 | 7 |
| 4 | 6 | 1 | 5 | 2 | 8 | 3 | 7 |
| 4 | 6 | 8 | 2 | 7 | 1 | 3 | 5 |
| 4 | 6 | 8 | 3 | 1 | 7 | 5 | 2 |
| 4 | 7 | 1 | 8 | 5 | 2 | 6 | 3 |
| 4 | 7 | 3 | 8 | 2 | 5 | 1 | 6 |
| 4 | 7 | 5 | 2 | 6 | 1 | 3 | 8 |
| 4 | 7 | 5 | 3 | 1 | 6 | 8 | 2 |
| 4 | 8 | 1 | 3 | 6 | 2 | 7 | 5 |
| 4 | 8 | 1 | 5 | 7 | 2 | 6 | 3 |
| 4 | 8 | 5 | 3 | 1 | 7 | 2 | 6 |
| 5 | 1 | 4 | 6 | 8 | 2 | 7 | 3 |
| 5 | 1 | 8 | 4 | 2 | 7 | 3 | 6 |
| 5 | 1 | 8 | 6 | 3 | 7 | 2 | 4 |
| 5 | 2 | 4 | 6 | 8 | 3 | 1 | 7 |
| 5 | 2 | 4 | 7 | 3 | 8 | 6 | 1 |
| 5 | 2 | 6 | 1 | 7 | 4 | 8 | 3 |
| 5 | 2 | 8 | 1 | 4 | 7 | 3 | 6 |
| 5 | 3 | 1 | 6 | 8 | 2 | 4 | 7 |
| 5 | 3 | 1 | 7 | 2 | 8 | 6 | 4 |
| 5 | 3 | 8 | 4 | 7 | 1 | 6 | 2 |
| 5 | 7 | 1 | 3 | 8 | 6 | 4 | 2 |
| 5 | 7 | 1 | 4 | 2 | 8 | 6 | 3 |
| 5 | 7 | 2 | 4 | 8 | 1 | 3 | 6 |
| 5 | 7 | 2 | 6 | 3 | 1 | 4 | 8 |
| 5 | 7 | 2 | 6 | 3 | 1 | 8 | 4 |
| 5 | 7 | 4 | 1 | 3 | 8 | 6 | 2 |
| 5 | 8 | 4 | 1 | 3 | 6 | 2 | 7 |
| 5 | 8 | 4 | 1 | 7 | 2 | 6 | 3 |
| 6 | 1 | 5 | 2 | 8 | 3 | 7 | 4 |
| 6 | 2 | 7 | 1 | 3 | 5 | 8 | 4 |
| 6 | 2 | 7 | 1 | 4 | 8 | 5 | 3 |
| 6 | 3 | 1 | 7 | 5 | 8 | 2 | 4 |
| 6 | 3 | 1 | 8 | 4 | 2 | 7 | 5 |
| 6 | 3 | 1 | 8 | 5 | 2 | 4 | 7 |
| 6 | 3 | 5 | 7 | 1 | 4 | 2 | 8 |
| 6 | 3 | 5 | 8 | 1 | 4 | 2 | 7 |
| 6 | 3 | 7 | 2 | 4 | 8 | 1 | 5 |
| 6 | 3 | 7 | 2 | 8 | 5 | 1 | 4 |
| 6 | 3 | 7 | 4 | 1 | 8 | 2 | 5 |
| 6 | 4 | 1 | 5 | 8 | 2 | 7 | 3 |
| 6 | 4 | 2 | 8 | 5 | 7 | 1 | 3 |
| 6 | 4 | 7 | 1 | 3 | 5 | 2 | 8 |
| 6 | 4 | 7 | 1 | 8 | 2 | 5 | 3 |
| 6 | 8 | 2 | 4 | 1 | 7 | 5 | 3 |
| 7 | 1 | 3 | 8 | 6 | 4 | 2 | 5 |
| 7 | 2 | 4 | 1 | 8 | 5 | 3 | 6 |
| 7 | 2 | 6 | 3 | 1 | 4 | 8 | 5 |
| 7 | 3 | 1 | 6 | 8 | 5 | 2 | 4 |
| 7 | 3 | 8 | 2 | 5 | 1 | 6 | 4 |
| 7 | 4 | 2 | 5 | 8 | 1 | 3 | 6 |
| 7 | 4 | 2 | 8 | 6 | 1 | 3 | 5 |
| 7 | 5 | 3 | 1 | 6 | 8 | 2 | 4 |
| 8 | 2 | 4 | 1 | 7 | 5 | 3 | 6 |
| 8 | 2 | 5 | 3 | 1 | 7 | 4 | 6 |
| 8 | 3 | 1 | 6 | 2 | 5 | 7 | 4 |
| 8 | 4 | 1 | 3 | 6 | 2 | 7 | 5 |

  [1]: http://sqlfiddle.com/#!9/2a756f/1
  [2]: http://sqlfiddle.com/#!9/2a756f/1/0
