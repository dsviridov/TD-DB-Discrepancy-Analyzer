TD-DB-Discrepancy-Analyzer
==========================

TD DB Discrepancy Analyzer (TDDBDA or simply DA) is a tool for searching and analysis discrepancies between Teradata environments.

- the tool have been being developed taking into account Teradata RDBMS features;
- the tool supports a DB/user hierarchical structure;
- the tool supports reconciliation of environments on different TD servers (an access to the servers via jdbc is needed);
- the tool supports reconciliation of environments with different DB prefixes;

DA capabilities
===============

DB/users structure:
-------------------
DA takes into account DatabaseName, OwnerName, DBKind from dbc.Databases while looking for discrepancies in DB/users structures.

Tables
------
While looking for discrepancies in Tables, the tool analyzes:
- if necessary tables present in the target environment;
- if excessive tables exist in the target environment;
- tables structure taking into account the following fields: 
  - ColumnId,
  - ColumnName,ColumnType, 
  - ColumnLength, 
  - DefaultValue, 
  - Nullable, 
  - DecimalTotalDigits,
  - DecimalFractionalDigits, 
  - UpperCaseFlag, 
  - Compressible,
  - CompressValue, 
  - ColumnConstraint, 
  - ConstraintCount,
  - CharType, 
  - IdColType, 
  - CompressValueList,
  - TimeDimension.

Views
-----
While looking for discrepancies in Views, DA analyzes the following:
- if necessary views exist in the target environment;
- if excessive views exist in the target environment;
- views structure (the same fields are taken into account as in case of tables);
- comparison of DDL of views creation (different DB prefixes are taken into account).

Macro
-----
DA analyzes al,ost the same as it does for Views.
One exception: instead of views structure DA analyzes Macro parameters.

Stored Procedures (SP)
----------------------
DA analyses almost the same as it does for Views.
One exception: instead of views structure DA analyzes SP parameters.

Trigger
-------
Not realized yet but it can be easily realized the same way as it was done for Macro and SP.


DA Roadmap
==========
- Statistical (reference) data analysis;
- DDL/DML code generation to sync the target environment in line with the standard one.
- a mechanizm to select items to compare (exclude/include lists/expression);

Technologies used
=================
- Pentaho PDI Community Edition (LGPL) http://community.pentaho.com/;
- Teradata JDBC Driver.

Requirements to the execution environment
=========================================
- OS: Originally developed and tested on Linux SLES 10 SP1 (Teradata Express). At the moment, there is no fundamental problems of adapting solutions to run on Windows.
- Sun / Oracle Java (TM) Runtime Environment 6 (version> = 1.6.0.u26);
- Pentaho Data Integration Community Edition (version> = 4.2.0);
- Teradata JDBC Driver (version> = 14.00.00).
