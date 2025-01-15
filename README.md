# Data-dictionary1
                       
1) Data Dictionary is also called ABAP Dictionary or DDIC.

   SE11 -> Transaction code for Data Dictionary or ABAP Dictionary.
   SE16->  Transaction code for Data Browser.
   SE16N-> New Version of SE16

2) Domain -> Tells us about the technical characteristics of a Field/Column.
    Technical characteristics -> Data type, length.

3) Data Element -> How a field/column will be visible to end user?

4) MANDT -> Client number of SAP system.

  Tables having MANDT field are called as client dependent tables or Client-Specific tables..
  Tables does not have MANDT field are called as Client Independent tables. 

5)  Data browser/Table view maintenace options ->
    Display/Maintenance allowed
    Display/Maintenance not allowed
    Display/Maintenance allowed with restrictions

6) Size Category -> A table can store how many number of records.

7)  Types of SAP Data ->
    Master Data-> Which is accessed very frequenty, but changed very rarely. 
    Transaction Data-> Which is always changing, number of records are continuously increasing.
    Configuration Data->Is something which we can customize,
                        Customizing depends on the business Scenario and customer requirements.

   Example -> Company ABC
  
              Master Data -> 
              Employee Data of the Company ABC

              Transaction Data ->
              Transactions in the Company(Banking transactions,Revenue transactions).

              Configuration Data->
             (Employee Designation-> Senior Consultant( Vehicle allowance applicable)
             (Employee Designation-> other than Senior consultant( Vehicle allowance not applicable).

8) Data Class -> Tells us in which portion of database the table data will get store. 

9) Delivery class-> It is used for controlling data transport of tables during installation,
                    upgrade and transporting between customer systems.  
                          
10) TMG( Table Maintenance Generator)
    Authorization group : &NC&( Any user can maintain the data).
    Single Step: Only overview screen is applicable
    Two Step :  Both Overview screen and single screen are applicable.

11) We can maintain data with the help of SM30.

12) Important Points related to TMG.
    a) Data browser/Table view maintenace options needs to be Display/Maintenance allowed.
    b) Whenever you add new columns/fields to the table after generation of TMG, The newly added fields
       will not appear automatically while maintaining data with the help of SM30. 
       We need to delete the TMG and generate it again.
    c) Deleting the TMG never delete the table data.
    d) To delete the TMG, Open the table in Change Mode, otherwise delete button will not be visible.         


13) Shortcuts -  CTRL + S = SAVE
                 CTRL + F2 -> Syntax Check
                 CTRL + F3 -> Activate
                 CTRL + SHIFT + F10 -> To check the contents of the table.

 
                                        Topic : Primary-Foreign Key Relationship

Primary Key of one table act as a Foreign key in another table.

( Data/Record/Row/Tuple will be always in the primary key table, It may or may not in the foreign key table)

Pre-requisite - Tables should have a common column/field.

Cardinality -> Number of records in key table, correponds to how many number of records in to secondary/foreign key table. 

Topic : Initial Values Check box in Table

1) We can select the checkbox Initial values for table fields, then the type dependent NOT NULL value be 
       assigned to that field and the flag for NOT NULL is set to true on database.
     
      Path to check : Utilities->Databaseobject->Display) - Refer column NOT NULL and Default.     
 
2)Many databases, will simply initialize the value of a field as NOT NULL even if we are not selecting this checkbox.
    
    Scenario: Suppose we added a new column NEW_1 to table ZTORDH_78 and for NEW_1 , the NOT NULL flag is true.
    First Query will not return any result and the second query will return the result.
    DATA : lt_ordh_78 TYPE TABLE OF ZTORDH_78.
            SELECT * FROM  ZTORDH_78
            INTO TABLE lt_ordh_78
            WHERE NEW_1 IS NULL.    "No Output

    DATA : lt_ordh_78 TYPE TABLE OF ZTORDH_78.
            SELECT * FROM  ZTORDH_78
            INTO TABLE lt_ordh_78
            WHERE NEW_1 = ' '.       "  Output

    DATA : lt_ordh_78 TYPE TABLE OF ZTORDH_78.
            SELECT * FROM  ZTORDH_78
            INTO TABLE lt_ordh_78
            WHERE NEW_1 IS NOT NULL.    "  Output

  Topic : Types of SAP Database tables

1) Transparent table - There is 1:1 relationship between the ABAP dictionary and the database.( One table in ABAP dictionary corresponds to one table in database)
2) Pooled table - There is N:1 relationship between the ABAP dictionary and the database.( Many tables in ABAP dictionary corresponds to one table in database)
3) Cluster table - There is N:1 relationship between the ABAP dictionary and the database.( Many tables in ABAP dictionary corresponds to one table in database )

Pooled -> Primary-foreign key relationship is not required.
Cluster -> Primary-foreign key relationship is mandatory.

Structure of a Pooled table at the database layer - Tabname Varkey Dataln vardata
Structure of a cluster table at the database layer - Key Pageno Vardata       

Topic : Table Buffering

Buffer is a temperory storage on the application layer. 
It improves the performance when accessing the data records contained in the table. 

Buffering Options:

1) Buffering not allowed-> Table buffering is not performed for the table.
2) Buffering switched on-> Table buffering is performed for the table.
3) Buffering allowed, but switched off-> Buffer is allowed but it is switched OFF 
                                        and can be switched ON anytime according to the requirement of customer.
 
Types of Buffering:

1) Single Record buffering -> Single Record will be in the buffer.

When to Use Single Record Buffering ->

Single-record buffering should be used for tables where only a few records are accessed by specifying the complete key. 

Advantage -> It will ocucupy less memory on the application layer.
Disadvantage -> Number of iterations will not be reduced between Application layer and database layer, 
                if we are not fetching the same record.


2) Full Buffering -> Full table will be in the buffer.

When to Use Full Record Buffering->

When you decide to fully buffer a table, you must take into account the size of the table,  
Tables that are best suited to full buffering are frequently accessed and rarely changed.

A table which stores transaction data should not be opted for Full buffering.

Advantage -> Number of iterations between Application and database layer will  be significantly reduced.
Disadvantage -> It will occupy more memory on the application Layer.


3) Generic area buffering -> All Records matches the generic key are loaded in the buffer.


When To Use Generic Buffering:

For Generic areas( Language Dependent tables)

Imp Point : The numbers of key field for a generic area buffering is less than the primary keys of the table.

Transaction Code to check the Buffer -> AL12( Path : Monitor->Buffers->Table Buffer->

Topic : Structures

Structures ->  Is a collection of fields/columns of different data type or similar data type.

ZEMP -> EID -> N(10)
        ENAME ->C(40)

ZEMP1 ->EID -> N(10)
        ESAL ->N(10)

Difference between table & Structure -> Table has data , Structure does not have any data.


Include  -> 1) It is a reusebale Structure.
            2) We can insert the include structure at any point.
            3) It is applicable to customer specific tables, It is not applicable to SAP specific tables.


Append  -> 1) It is not a reuseable structure.
           2) It always inserts at the last.
           3) It is applicable to both customer specific tables and SAP tables.


