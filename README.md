# Data-dictionary1
 Data Dictionary                         


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
