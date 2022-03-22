# SQL To Datagridview
### Setup and Read Database to Store at Datagridview
```
private void FillTable()
{
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
}
```
### Update to database to multiple column
```
using (SqlConnection connect = new SqlConnection(@"Data Source=" + machname + "\\SQLEXPRESS;Initial Catalog=MachineDatabase;Integrated Security=True")) 
    { 
        connect.Open(); 
        string sql; 
        SqlCommand com; 
        SqlDataAdapter adap = new SqlDataAdapter(); 
        sql = "Update [MachInfo] SET OperationProgram = @_opsprog, OperationStatus = @_opstat Where id = 1"; 
        com = new SqlCommand(sql, connect); 
        adap.InsertCommand = new SqlCommand(sql, connect); 
        adap.InsertCommand.Parameters.Clear(); 
        adap.InsertCommand.Parameters.AddWithValue("@_opsprog", execProgram); 
        adap.InsertCommand.Parameters.AddWithValue("@_opstat", ncstat); 

        adap.InsertCommand.ExecuteNonQuery(); 
        com.Dispose(); 
    }
