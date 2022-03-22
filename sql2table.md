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
