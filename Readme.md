# Course Database Project


## Process 1: Designing the Boyce-Codd normalized ERD
1. <b>Filter through the data to design a BC normalized ERD. We designed the strong entity tables first. </b>
    1. The strong entities were the PROGRAM, INSTRUCTOR, and LOCATION.
2. <b>The designed the weak entities (entities on the many side of one-to-many relationships). </b>
    1. These entities were the tables CATALOG_COURSE, OFFERINGS_COURSE, and MEETINGS_COURSE. Each of these tables could not be uniquely defined without one of the strong entities in step 1-1.
3. <b>Note: We resolved many of the normalization requirements by creating unique, auto-incrementing ID’s for each table row. </b>
4. (Link to ERD)

## Process 2: Creating the normalized database and importing the data
1. <b>Load the SQL extension</b>
    1. Importing the data into the database so that we can populate the table rows
2. <b>Connecting SQLite to the CourseData database</b>
3. <b>Using PRAGMA to ensure the datasets are properly imported</b>
4. <b>Using the CREATE TABLE command to add tables to our database - first the strong entities, then the weak entities.</b>
    1. Strong entity tables to be created first - INSTRUCTOR, LOCATION, PROGRAM
    2. Weak entity tables to be created after - CATALOG_COURSE (with a FK from the PROGRAM table), OFFERINGS_COURSE (with FK’s from the CATALOG_COURSE table and INSTRUCTOR table), and finally MEETINGS_COURSE (with FK’s from the LOCATION and OFFERINGS_COURSE table).
5. <b>Using the INSERT INTO commands to move data from the corresponding datasets into each table. We populated the strong entities first, then the weak entities (due to FK reliance). We used the same order as the table creations to minimize any potential issues. </b>
6. <b>Dropping the CSV datasets and vacuuming the data to clean up space issues.</b>
7. (Link to CourseDataETL)

## Process 3: Testing data integrity of the database
1. <b>Load the SQL extension</b>
2. <b>Connecting SQLite to the CourseData database</b>
3. <b>Using PRAGMA to ensure the table columns have been created correctly, and that each FK constraint has an associated ‘NOT NULL’ value.</b>
4. <b>Random data tests</b>
    1. Testing strong entity tables to ensure data imported correctly
    2. Testing some of the weak entities (OFFERING_COURSE in this case) to see if there is any data mismatch
    3. Digging into a potential data mismatch error. Data appears to be fine, however, noting a possible need to remove inaccurate data from the dataset in the future.
    4. Testing more complicated joins and ensuring that the data appears to be pulling correctly for the weakest entity (MEETINGS_COURSE).
5. (Link to CourseDataTests)


## Process 4: Designing a scehma data warehouse
1. (Link to star schema ERD)

## Process 5: Creating a star scehma data warehouse
1. <b>Load the SQL extension</b>
2. <b>Connecting SQLite to the CourseDataWarehouse database</b>
3. <b>Using the CREATE TABLE command to add tables to our database - first the dimension tables, then the fact table</b>
    1. Dimension tables to be created first - INSTRUCTOR_WH, LOCATION_WH, PROGRAM_WH, CATALOG_COURSE_WH, TIME_CODE_WH, and    TERM_WH
    2. Create the fact table REG_COURSE_WH   
4. <b>Using the INSERT INTO commands to move data from the corresponding datasets into each table. We populate the tables in the same order that they are created.</b>
    1. Dimension tables populated first
    2. Before populating the fact table, we test a select query with a large number of joins to ensure that the data is pulling correctly before we insert it. Once we are satisfied with the testing, we populate the fact table.   
5. <b>COUNT the rows on the fact table to ensure that the number of total rows lines up with the rows added.</b>
6. (Link to CourseDataWarehouse)