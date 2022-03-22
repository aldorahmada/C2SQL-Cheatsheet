# SQL Cheatsheet
## SQL to Datagridview
### Inserting SQL data to datagridview by filling datatable 
```
using (SqlConnection connect = new SqlConnection(@"Data Source="+ Machine_Name +"\\SQLEXPRESS;Initial Catalog=DatabaseName;Integrated Security=True"))
{
    connect.Open();
    string sql;
    SqlCommand com;
    SqlDataAdapter adap = new SqlDataAdapter();
    DataTable dt = new DataTable();
    sql = "SELECT * FROM [dbo].[TableName]";
    com = new SqlCommand(sql, connect);
    adap.SelectCommand = new SqlCommand(sql, connect);
    adap.Fill(dt);
    dataGridView1.DataSource = dt;
}
```
## Database Update
### Update to database to multiple column
```
using (SqlConnection connect = new SqlConnection(@"Data Source=" + MachineName + "\\SQLEXPRESS;Initial Catalog=DatabaseName;Integrated Security=True")) 
{ 
    connect.Open(); 
    string sql; 
    SqlCommand com; 
    SqlDataAdapter adap = new SqlDataAdapter(); 
    sql = "Update [TableName] SET Column1 = @_column1, Column2 = @_column2 Where id = 1"; 
    com = new SqlCommand(sql, connect); 
    adap.InsertCommand = new SqlCommand(sql, connect); 
    adap.InsertCommand.Parameters.Clear(); 
    adap.InsertCommand.Parameters.AddWithValue("@_column1", variable1); 
    adap.InsertCommand.Parameters.AddWithValue("@_column2", variable2); 

    adap.InsertCommand.ExecuteNonQuery(); 
    com.Dispose(); 
}
```
## Get Cell Data
### get single data with specific column and row
```
using (SqlConnection connect = new SqlConnection(@"Data Source=" + MachineName + "\\SQLEXPRESS;Initial Catalog=MachineDatabase;Integrated Security=True"))
{
    connect.Open();
    string sql;
    SqlCommand com;
    SqlDataAdapter adap = new SqlDataAdapter();
    sql = "SELECT TOP 1[ColumnName] FROM[dbo].[TableName]";
    com = new SqlCommand(sql, connect);
    adap.SelectCommand = new SqlCommand(sql, connect);
    SqlDataReader rdr = com.ExecuteReader();
    if (rdr.Read())
    {
        val = rdr.GetValue(0).ToString();//Send the data to variable
    }
    rdr.Close();
    com.Dispose();
} 
```
