package n5;

import java.io.*;
import java.sql.*;
import java.util.*;
public class n9 {
    public static void main(String[] args) {
            List <String>data = new ArrayList<String>();
            try {
                    Connection con = null;
                    Class.forName("com.mysql.cj.jdbc.Driver");
                    con = DriverManager.getConnection("jdbc:mysql://localhost:3306/d1", "root", "08.09.1994Ww");
                    Statement st = con.createStatement();    
                    ResultSet rs= st.executeQuery("SELECT * from student where departmentId='2'");
                    //ResultSet rs = st.executeQuery("SELECT departmentId,count( * ) studentId  FROM `student` WHERE departmentId='2' GROUP BY studentId");
                   //ResultSet rs=st.executeQuery("Select * from student,count(*) studentId where departmentId='1'");
                    //String s1="SELECT departmentId,count( * ) AS studentId  FROM `student` WHERE departmentId='1' GROUP BY studentId";
					//st.executeQuery(s1);
					//System.out.println(s1);

                    while (rs.next()) {
                            String id = rs.getString("studentId");
                            String fname = rs.getString("fullName");
                            String lname = rs.getString("lastName");
                            String did= rs.getString("departmentId");
                            String jd = rs.getString("joiningDate");
                            String sd = rs.getString("studentDob");
                            String mn = rs.getString("mobileNo");
                            String em = rs.getString("email");
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
            } catch (IOException e) {
            }
    }
}