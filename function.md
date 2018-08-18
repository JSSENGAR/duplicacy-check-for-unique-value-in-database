# duplicacy-check-for-unique-value-in-database
Function to avoid duplicate entry for any column  of any table 
//Function to avoid duplicate entry for any column  of any table 
	
	public string dup_chk(string tbn, string fn, string v)
        {
            con.Close();
            con.ConnectionString = sqlcs();
            con.Open();
            string tpd = "";
            SqlCommand cmdchk = new SqlCommand("select " + fn+ " from " + tbn +" where " + fn + "='"+v+"'", con);
            SqlDataReader sdrtpd = cmdchk.ExecuteReader();
            sdrtpd.Read();

            if (sdrtpd.HasRows)
                tpd = sdrtpd[fn].ToString() + " - Already Exist";
            else
                tpd = v;

            sdrtpd.Close();
            con.Close();
            return tpd;
        }
