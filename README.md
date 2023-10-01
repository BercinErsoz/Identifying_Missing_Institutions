# Identifying_Missing_Institutions
#Detection of Institutions That Do Not Send Their Forms on Time



    import pandas as pd
    import getpass
    import pyodbc
    user_id = input(\"kullanıcı adını giriniz: \")
    password = getpass.getpass(\"şifre giriniz: \")
  
   
    date = input(\"this week as 'YYYY-MM-DD': \")
    pre_date= input(\"previous week as 'YYYY-MM-DD': \")
    
    
    connection_str = f"""",
    Driver={{IBM DB2 ODBC DRIVER - DB2COPY1}};",
    DBALIAS=PROD;,
    Uid={user_id};,
    Pwd={password};,
   
    db_connection = pyodbc.connect(connection_str)
 
    "sql_command =  "SELECT TARIH, ARACI_KURUM_KOD \"+ \\",
    "                      \"FROM BVIYYMK.TARKMD302H \" + \\",
    "                      f\"WHERE TARIH = '{tarih}' \""
   
    "sql_command1 =  \"SELECT TARIH, ARACI_KURUM_KOD \"+ \\\n",
    "                      \"FROM BVIYYMK.TARKMD302H \" + \\\n",
    "                      f\"WHERE TARIH = '{tarih_gecen_hafta}'\""
  
    "df= pd.read_sql(sql_command, db_connection)"
  
    "df1= pd.read_sql(sql_command1, db_connection)"
 
    "set(df1.ARACI_KURUM_KOD).difference(set(df.ARACI_KURUM_KOD))"
  
