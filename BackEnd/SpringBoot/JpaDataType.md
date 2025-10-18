# JPA DB Data Type To Java Type

## 1. DB별 Type
|Java Type |Java DB, Derby, CloudScape |Oracle |MS-SQL Server |MySQL Server |DB2 |Sybase|
|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
|boolean, java.lang.Boolean|SMALLINT|NUMBER(1)|BIT|TINYINT(1)|SMALLINT|BIT|
|int, java.lang.Integer|INTEGER|NUMBER(10)|INTEGER|INTEGER|INTEGER|INTEGER|
|long, java.lang.Long|BIGINT|NUMBER(19)|NUMERIC(19)|BIGINT|INTEGER|NUMERIC(19)|
|float, java.lang.Float|FLOAT|NUMBER(19,4)|FLOAT(16)|FLOAT|FLOAT|FLOAT(16)|
|double, java.lang.Double|FLOAT|NUMBER(19,4)|FLOAT(32)|DOUBLE|FLOAT|FLOAT(32)|
|short, java.lang.Short|SMALLINT|NUMBER(5)|SMALLINT|SMALLINT|SMALLINT|SMALLINT|
|byte, java.lang.Byte|SMALLINT|NUMBER(3)|SMALLINT|SMALLINT|SMALLINT|SMALLINT|
|java.lang.Number|DECIMAL|NUMBER(38)|NUMERIC(28)|DECIMAL(38)|DECIMAL(15)|NUMERIC(38)|
|java.math.BigInteger|BIGINT|NUMBER(38)|NUMERIC(28)|BIGINT|BIGINT|NUMERIC(38)|
|java.math.BigDecimal|DECIMAL|NUMBER(38)|NUMERIC(28)|DECIMAL(38)|DECIMAL(15)|NUMERIC(38)|
|java.lang.String|VARCHAR(255)|VARCHAR(255)|VARCHAR(255)|VARCHAR(255)|VARCHAR(255)|VARCHAR(255)|
|char, java.lang.Character|CHAR(1)|CHAR(1)|CHAR(1)|CHAR(1)|CHAR(1)|CHAR(1)|
|byte[], java.lang.Byte[], java.sql.Blob|BLOB(64000)|LONG RAW|IMAGE|BLOB(64000)|BLOB(64000)|IMAGE|
|char[], java.lang.Character[], java.sql.Clob|CLOB(64000)|LONG|TEXT|TEXT(64000)|CLOB(64000)|TEXT|
|java.sql.Date, java.time.LocalDate|DATE|DATE|DATETIME|DATE|DATE|DATETIME|
|java.sql.Time, java.time.LocalTime|TIME|DATE|DATETIME|TIME|TIME|DATETIME|
|java.sql.Timestamp,  java.time.LocalDate|TIMESTAMP|DATE|DATETIME|DATETIME|TIMESTAMP|DATETIME|

## 2. Mapping Java to Database.com Data Types
|Java Data Type|Database.com Data Type|Standard JPA Annotation|
|:--------:|:--------:|:--------:|
|boolean, Boolean|Checkbox|N/A|
|byte, Byte|Text (255)|@Column(length=255)|
|char, Character|Text (255)|@Column(length=255)|
|short, Short|Number (6, 0)|@Column(precision=6, scale=0)|
|int, Integer|Number (11, 0)|@Column(precision=11, scale=0)|
|long, Long|Number (18, 0)|@Column(precision=18, scale=0)|
|double, Double|Number (16, 2)|@Column(precision=16, scale=2)|
|Float|Number (16, 2)|@Column(precision=16, scale=2)|
|String|Text (255)|@Column(length=fieldLength)|
|java.util.Date|Date|@Temporal(TemporalType.DATE)|
|Calendar|Date/Time|@Temporal(TemporalType.TIMESTAMP)|
|GregorianCalendar|Date/Time|@Temporal(TemporalType.TIMESTAMP)|
|BigInteger|Number (18, 0)|@Column(precision=18, scale=0)|
|BigDecimal|Currency|@Column(precision=16, scale=2)|
|byte[]|See Binary (Base64) Fields.|N/A|
|String[]|Picklist (Multi-Select) for selected values|@Enumerated(EnumType.STRING) OR @Enumerated(EnumType.ORDINAL)|
|enum|Picklist for available values|N/A|
|URL|URL|N/A|
