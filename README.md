# Identifying_Missing_Institutions
#Detection of Institutions That Do Not Send Their Forms on Time



    import pandas as pd
    import getpass
    import pyodbc
    user_id = input("user name: ")
    password = getpass.getpass("your password: ")
  
   
    date = input("this week as 'YYYY-MM-DD': ")
    pre_date= input("previous week as 'YYYY-MM-DD': ")
    
#DB2 connection with user_id and password 


    connection_str = f""",
    "Driver={{IBM DB2 ODBC DRIVER - DB2COPY1}};",
    "DBALIAS=PROD;",
    "Uid={user_id};",
    "Pwd={password};","""
   
    db_connection = pyodbc.connect(connection_str)
 
    sql_command =  "SELECT TARIH, ARACI_KURUM_KOD " + \,
                          "FROM BVIYYMK.TARKMD302H " + \,
                          "WHERE TARIH = '{date}' "
   
    sql_command1 =  "SELECT TARIH, ARACI_KURUM_KOD " + \,
                          "FROM BVIYYMK.TARKMD302H " + \,
                         "WHERE TARIH = '{pre_date}' ""
  
    df= pd.read_sql(sql_command, db_connection)
  
    df1= pd.read_sql(sql_command1, db_connection)

#Comparison of institution names in the Inst_code column in two consecutive weeks
 
    set(df1.Inst_code).difference(set(df.Inst_code))
  
