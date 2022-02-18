package n4;

import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileWriter;
import java.io.IOException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class n10 {

	public static void main(String[] args) {  
		
		try{
			Statement st=null;
			try {
				Class.forName("com.mysql.cj.jdbc.Driver").newInstance();
				Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/d1", "root", "08.09.1994Ww");
				st=con.createStatement();
				//Statement stmt=con.createStatement();
			}
			catch(Exception e) {
				e.printStackTrace();
			}
			try {  
				//con=getConnection();
				//con.setAutoCommit(false);
				File f1 = new File("D:\\input1.txt");    
				Scanner dataReader = new Scanner(f1);  
				while (dataReader.hasNextLine()) {  
					String[] fileData = dataReader.nextLine().split("\\s+");

					int studentId = Integer.valueOf(fileData[0]);
					String fullName = fileData[1];
					String lastName = fileData[2];
					String departmentId = fileData[3];
					String joiningDate = fileData[4];
					String studentDob = fileData[5];
					String mobileNo = fileData[6];
					String email = fileData[7];
					
					
					System.out.println("StudentId: "+studentId+ ", fullName: "+fullName+",lastName: "+lastName+",Department: "+departmentId+",joining date: "+joiningDate+",student Dob: "+studentDob+",mobileNo: "+mobileNo+",email: "+email+""); 
					String qry ="insert into d1.student values ("+studentId+","+"'"+fullName+" '"+","+"'"+lastName+"'"+","+"'"+departmentId+"'"+","+"'"+joiningDate+"'"+","+"'"+studentDob+"'"+","+"'"+mobileNo+"'"+","+"'"+email+"'"+")";
					System.out.println(qry);
					st.executeUpdate(qry);  
					String sql1="update d1.student set fullName='Vikky' where lastName='vikki'";
					st.executeUpdate(sql1);
				//pstmt=con.prepareStatement("insert into DataFiles(id,fileName,fileBody)values(?,?,?)");
				}  
				dataReader.close();  
			} catch (Exception exception) {  
				System.out.println("Unexcpected error occurred!");  
				exception.printStackTrace();  
			}  

			File f2 = new File("D:\\delete.txt");    
			Scanner dataReader1;
			try {
				dataReader1 = new Scanner(f2);
				while (dataReader1.hasNextLine()) {  
					String fileData = dataReader1.nextLine();
					int studentId = Integer.valueOf(fileData);
					String sql = "DELETE FROM student WHERE studentId = "+studentId+"";
					System.out.println(sql);
					st.executeUpdate(sql);
					
					
				}
			} catch (Exception e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			} 
				
					
	/*List <String>data = new ArrayList<String>();
            try {   
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
            } catch (IOException e) {
            	System.out.println(e);
            }
            finally {
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
            }*/
	
			
		}
		finally {
		
		}
	}
}
		
	
	


// 6 a 
//String sql2=SELECT * from student COUNT(studentId), studentId FROM d1.student GROUP BY departmentId;
//ResultSet rs=st.executeQuery(sql2);

// }  

//}




