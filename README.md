# MigrationTask_OracleToPostgreSQL
Migrating the Oracle HR database to PostgreSQL

The task is:
1. Download a Virtual machine (f.e., Virtual Box) and image with installed Oracle DBMS (f.e., https://www.oracle.com/database/technologies/databaseappdev-vm.html)
2. Set up on local machine.
3. Work with the HR database:
   3.1 Add creation_date and update_date columns to all tables in HR.
   3.2 Fill in creation_date values from December, 2022. Every table should have 5 separate date values for their records.
   3.3 Create a trigger for each table - on insert: if creation_date != sysdate then creation_date := sysdate;
                                         on update: update_date := sysdate;
   3.4 Create a package export_hr with public procedure start_daily_export with 2 input parameters:
     p_date_export of date datatype with defaul value of sysdate and p_is_fullexport with of number datatype with default value of 0.
   3.5 Realize the procedural logic:
     When starting start_daily_export procedure with p_is_fullexport = 1:
     - The structure of all HR tables should be exported to files (a file for each table with name table_nameoftable_dateofexport(.txt/.sql) or other file format).
     - All data for each table to be exported into a separate file per table with name: data_nameoftable_dateofexport with file format of my choosing.
       When starting start_daily_export procedure with p_is_fullexport = 0:
     - Export the data of the tables in HR which are "newer" then the last exported records or old records with changes in them.
       Again, a single file per table with name data_nameoftable_dateofexport with file format of my choosing.
4. The files should be copied to a machine (it may be virtual env.) with working PostgreSQL DBMS.
5. There should be a procedural logic of loading the file content into a PostgreSQL database.
