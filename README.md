# Week-4-SQL-Exercise
MariaDB [(none)]> use foy
Database changed

# 1
MariaDB [foy]> create table stateterritories (State varchar(30), Abbreviation varchar(10) primary key);
Query OK, 0 rows affected (0.011 sec)

MariaDB [foy]> LOAD DATA LOCAL INFILE 'C:\\Users\\foyje\\Downloads\\States_Territories.csv' INTO TABLE Stateterritories FIELDS TERMINATED BY ',' ENCLOSED by '"' LINES TERMINATED BY '\n';
Query OK, 58 rows affected (0.005 sec)
Records: 58  Deleted: 0  Skipped: 0  Warnings: 0

# 2
MariaDB [foy]> SELECT state, COUNT(*) AS total FROM vets GROUP BY state ORDER BY COUNT(*) DESC;
+-------+-------+
| state | total |
+-------+-------+
| CA    |  5575 |
| NY    |  4120 |
| TX    |  3414 |
| PA    |  3141 |
| OH    |  3092 |
| IL    |  2930 |
| MI    |  2654 |
| FL    |  1950 |
| NC    |  1609 |
| GA    |  1583 |
| IN    |  1531 |
| NJ    |  1484 |
| MO    |  1411 |
| MA    |  1322 |
| VA    |  1304 |
| TN    |  1291 |
| AL    |  1207 |
| WI    |  1160 |
| MN    |  1072 |
| KY    |  1055 |
| WA    |  1050 |
| MD    |  1014 |
| OK    |   988 |
| SC    |   895 |
| LA    |   882 |
| IA    |   852 |
| WV    |   731 |
| OR    |   709 |
| MS    |   637 |
| KS    |   626 |
| AZ    |   622 |
| CO    |   619 |
| CT    |   612 |
| AR    |   588 |
| NM    |   399 |
| NE    |   395 |
| UT    |   365 |
| PR    |   345 |
| ME    |   342 |
| HI    |   277 |
| MT    |   268 |
| DC    |   241 |
| NH    |   227 |
| ID    |   217 |
| RI    |   207 |
| ND    |   198 |
| SD    |   195 |
| NV    |   151 |
| DE    |   122 |
| WY    |   119 |
| VT    |   100 |
| GU    |    70 |
| XC    |    58 |
| AK    |    57 |
| XP    |    32 |
| VQ    |    15 |
| XG    |     7 |
| XM    |     5 |
| SO    |     4 |
| XJ    |     4 |
| XN    |     3 |
| ZZ    |     3 |
| XE    |     3 |
| XB    |     3 |
| XI    |     2 |
| XF    |     2 |
| CZ    |     2 |
| XS    |     1 |
| XA    |     1 |
+-------+-------+
69 rows in set (0.035 sec)

# 3
MariaDB [foy]> SELECT DISTINCT v.state FROM vets v LEFT JOIN stateterritories s on v.state = s.Abbreviation WHERE s.Abbreviation IS NULL;
+-------+
| state |
+-------+
| XP    |
| XJ    |
| VQ    |
| XS    |
| XC    |
| XB    |
| ZZ    |
| XI    |
| XN    |
| XE    |
| XG    |
| XM    |
| XF    |
| SO    |
| XA    |
| CZ    |
+-------+
16 rows in set (0.050 sec)

# 4 - mynewpaltz database added, student and eployee table added
MariaDB [foy]> SOURCE C:\\Users\\foyje\\Downloads\\StudentExample.sql;
MariaDB [mynewpaltz]> SOURCE C:\\Users\\foyje\\Downloads\\EmployeesDatabase.sql;
ERROR 1049 (42000) at line 3 in file: 'C:\\Users\foyje\Downloads\EmployeesDatabase.sql': Unknown database 'employee'
Query OK, 0 rows affected (0.006 sec)

Query OK, 0 rows affected (0.004 sec)

Query OK, 7 rows affected (0.001 sec)
Records: 7  Duplicates: 0  Warnings: 0

Query OK, 7 rows affected (0.001 sec)
Records: 7  Duplicates: 0  Warnings: 0

Query OK, 19 rows affected (0.001 sec)
Records: 19  Duplicates: 0  Warnings: 0

MariaDB [mynewpaltz]> show databases;
+--------------------+
| Database           |
+--------------------+
| foy                |
| information_schema |
| mynewpaltz         |
| mysql              |
| performance_schema |
| sys                |
| test               |
+--------------------+
7 rows in set (0.001 sec)

MariaDB [mynewpaltz]> show tables;
+----------------------+
| Tables_in_mynewpaltz |
+----------------------+
| coursetable          |
| departments          |
| employees            |
| enrollmenttable      |
| studenttable         |
+----------------------+
5 rows in set (0.001 sec)

MariaDB [mynewpaltz]>
