package n5;

import java.io.*;
import java.sql.*;
import java.util.*;
public class n11 {
    public static void main(String[] args) {
       
            //List <String>data = new ArrayList<String>();
            try {
                    Connection con = null;
                    PreparedStatement p = null;
                    Class.forName("com.mysql.cj.jdbc.Driver");
                    con = DriverManager.getConnection("jdbc:mysql://localhost:3306/d1", "root", "08.09.1994Ww");
                    Statement st = con.createStatement(); 
                   int n = st.executeUpdate("ALTER TABLE d1.student ADD departmentName int");
                  // int query1 = st.executeUpdate("Update d1.student Set departmentName ='CS' Where departmentId = '1'");
                   //int count = st.executeUpdate(query1);
                   //String sampleSqlStatement = "UPDATE d1.student" +
                    	//	"SET departmentName = 'CS' WHERE departmentId ='1'";
                   // int r=st.executeUpdate(sampleSqlStatement);
                  //  String sql = "insert into d1.student set departmentname='CS' where departmentId=1";
                  // st.executeUpdate(sql);
                  // String s= "insert into departmentName='CS' select * from d1.student where departmentId='1'";
                  //st.executeUpdate(s);
                   // String sql = "insert into d1.student set departmentName='CS' where departmentId='1'";
                    //st.executeUpdate(sql);
                    String sql ="update d1.student set departmentName='CS' where departmentId=1";           
                   // p = st.prepareStatement(sql);          
                    st.executeUpdate(sql);
                    st.close();
            }
                   // String query= "ALTER TABLE student ADD COLUMN departmentName varchar(255)";
      
                // executeUpdate() is used for INSERT, UPDATE,
                // DELETE statements.It returns number of rows
                // affected by the execution of the statement
               // Result str = st.executeUpdate(query);
                    

                    /*while (query.next()) {
                            String id = query.getString("studentId");
                            String fname = query.getString("fullName");
                            String lname = query.getString("lastName");
                            String did= query.getString("departmentId");
                            String jd = query.getString("joiningDate");
                            String sd = query.getString("studentDob");
                            String mn = query.getString("mobileNo");
                            String em = query.getString("email");
                            data.add(id + " " + fname + " " + lname + " " + did + " " + jd + " " + sd + " " + mn + " " + em);

                    }
                    writeToFile(data,"D:\\dept.txt");
                    rs.close();
                    st.close();
            } catch (Exception e) {
                    System.out.println(e);
            }
    }

    private static void writeToFile(java.util.List <String>list, String path) {
            BufferedWriter out = null;
            try {
                    File file = new File(path);
                    out = new BufferedWriter(new FileWriter(file, true));
                    for (String s : list) {
                            out.write(s);
                            out.newLine();

                    }
                    out.close();
            }*/ catch (Exception e) {
            	e.printStackTrace();
            }
    }
}

