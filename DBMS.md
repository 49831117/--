# Database Management System
資料庫管理系統，為使用者（或使用資料庫的應用程式）與資料庫間溝通的平台。

## 關聯式資料庫、非關聯式資料庫
1. 關聯式資料庫（Relational Database Management System, RDBMS）
    1. 資料是以一個或多個 table 存放
        > Records → Tables → Relational Database
    2. 資料間有明確關聯
    3. SQL（Structured Query Language）
        - 在 `table` 中取出滿足 `condition` 的資料
            ```SQL
            SELECT * FROM [TABLE_NAME] WHERE [COND];
            ```
        1. 
            ```SQL
            SELECT 
            PayType, COUNT(PayType)
            FROM JOBMAS left join JOBADD on JOBMAS.JOBID=JOBADD.JOBID left join JOBPAY on JOBMAS.JOBID=JOBPAY.JOBID 
            WHERE (Status = 'Done' AND CITY ='台北市' AND JOBTIME LIKE '%2018-09%') GROUP BY paytype;
            ```
        2. 
            ```SQL
            SELECT 
            PayType, 
            COUNT(CASE WHEN Status = 'Done' OR Status = 'Cancel' THEN 1 ELSE 0 END)'原始任務數(Done+Cancel)',
            COUNT(CASE WHEN Status = 'Done' THEN 1 ELSE 0 END)'完成任務數',
            COUNT(CASE WHEN Status = 'Done' AND ComeFrom LIKE '%AGC%' THEN 1 ELSE 0 END)'AGC完成任務數'
            FROM JOBMAS left join JOBADD on JOBMAS.JOBID=JOBADD.JOBID left join JOBPAY on JOBMAS.JOBID=JOBPAY.JOBID 
            WHERE (CITY ='台北市' AND JOBTIME LIKE '%2018-09%' AND JOBTIME LIKE '% 08:%');
            ```
2. NoSQL 非關聯式資料庫
    Not Only SQL, 不限定為「關聯式資料庫」的資料庫管理系統的統稱。
    操作上，NoSQL 不支援 SQL 語法與邏輯，不使用關聯模型、不需要固定結構（schema-free），若有需要仍可使用關聯模型與 schema。
    1. 文件資料庫（document database）：文件組成的集合（collection）放在一起。
        > 文件存成 `.json` 格式，而資料物件會由 `attribute-value pair` 或陣列組成。
    2. **不講求資料同步，只求最後結果一致。**
3. 應用程式與資料庫
    1. 當要在應用程式裡整合資料庫股臉系統時，需瞭解：
         - **How** 應用程式如何與資料庫溝通
         - **Which** 選擇用什麼資料庫
         - **Def** 如何在應用程式裡定義資料結構
    2. 與資料庫溝通：ODM、ORM
         > 物件映射（Object Mapping）：
         > 
         >主要是用程式語言裡的「物件」來包裝資料庫的 SQL，讓開發者可以直接使用物件導向的方式操作資料庫，增加易讀性、維護性，但也有人認為直接用資料庫管理系統的原生語言（如 SQL），才能確保操作時的效率與準確。
         1. 文件資料庫：ODM，Object Document Mapping
         2. 關聯式資料庫：ORM，Object Relational Mapping


ref:[SQL/NoSQL 是什麼？認識資料庫管理系統 DBMS](https://tw.alphacamp.co/blog/sql-nosql-database-dbms-introduction)