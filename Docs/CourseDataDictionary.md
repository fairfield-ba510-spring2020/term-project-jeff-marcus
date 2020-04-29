# Course Data Dictionary

## INSTRUCTOR Table:
- <b>IID</b>: This column is an auto-incremented primary key to uniquely identify each instructor.
- <b>Name</b>: This column provides a list of each unique instructor in the database.

## LOCATION Table
- <b>LID</b>: This column is an auto-incremented primary key to uniquely identify each location.
- <b>Location</b>: This column provides a list of each unique location in the database.

## PROGRAM Table
- <b>PID</b>: This column is an auto-incremented primary key to uniquely identify each location.
- <b>ProgramCode</b>: This column provides a list of each unique program code in the database.
- <b>ProgramName</b>: This column provides a list of each unique program name in the database.


## CATALOG_COURSE Table
- <b>CAID</b>: This column is an auto-incremented primary key to uniquely identify each catalog course.
- <b>CatalogID</b>: This column provides a list of each catalog ID associated with each program from the PROGRAM table.
- <b>ProgramName</b>: This column is a foreign key reference to the PROGRAM table to define the program for each instance of CAID.
- <b>Credits</b>: This column provides the number of course credits associated with each catalog course.
- <b>Title</b>: This column provides the title for each catalog course.
- <b>Attributes</b>: This column provides programs related to each one catalog course
- <b>Description</b>: This column provides a description of each catalog course selection.
- <b>Pre-reqs</b>: This column provides any (if applicable) pre-requisites for each catalog course.

## OFFERINGS_COURSE Table
- <b>COID</b>: This column is an auto-incremented primary key to uniquely identify each course offering.
- <b>CatalogID</b>: This column is a foreign key reference to the CATALOG_COURSE table to define each catalog associated with each instance of COID.
- <b>Name</b>: This column is a foreign key reference to the INSTRUCTOR table to define instructor name's associated with each instance of COID.
- <b>Meetings</b>: This column identifies the different meeting dates and times associated with each course offering. 
- <b>CRN</b>: This column identifies uniquely identifies each course number associated with each course offering.
- <b>Term</b>: This column identifies which school term is associated with each course offering.
- <b>Section</b>: This column identifies which section is associated with each course offering.
- <b>Cap</b>: This column identifies the max number of registrations for each course offering.
- <b>Act</b>: This column identifies the current number of registrations for each course offering.
- <b>Rem</b>: This column identifies the remaining available registration spots associated with each course offering.

## MEETINGS_COURSE Table
- <b>CMID</b>: This column is an auto-incremented primary key to uniquely identify each course meeting.
- <b>CRN</b>: This column is a foreign key reference to the OFFERINGS_COURSE table to define the course each meeting is for.
- <b>Location</b>: This column is a foreign key reference to the LOCATION table to define the location for each meeting.
- <b>Day</b>: This column provides the day (M - F) that each course meeting takes place on.
- <b>Start</b>: This column provides the starting date & time the course meets.
- <b>End</b>: This column provides the last date & time that the course meets.