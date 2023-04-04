# FirstProject
package connectionc;
import java.sql.*;
import java.util.Scanner;
import java.io.*;
public class ConnectionC{
    
    private String name;
    private String email;
    private String phonenumber;
    private String state;
    private String district;
    //private String problem;
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public String getPhonenumber() {
        return phonenumber;
    }

    public void setPhonenumber(String phonenumber) {
        this.phonenumber = phonenumber;
    }
    public String getState() {
        return state;
    }
    public void setState(String state) {
        this.state =state;
    }
    public String getDistrict() {
        return district;
    }
    public void setDistrict(String district) {
        this.district=district;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    public Connection con;
        public static void main(String[] args) throws ClassNotFoundException, SQLException{// throws ClassNotFoundException ,SQLException,UnsupportedOperationException {
        
            Scanner sc=new Scanner(System.in);
            ConnectionC obj=new ConnectionC();
        String myDriver="com.mysql.cj.jdbc.Driver";
        String myUrl="jdbc:mysql://localhost:3306/getconnect";
        String username="root";
        String mypassword="root";
        Class.forName(myDriver);
        Connection con;
        con = DriverManager.getConnection(myUrl,username,mypassword);
        try (Statement stmt = con.createStatement()) {
            DataInputStream KB=new DataInputStream(System.in);
        System.out.println("Enter your name:");
        String name=sc.nextLine();
        obj.setName(name);
        System.out.println("Enter your email id:");
        String email=sc.nextLine();
        obj.setEmail(email);
        System.out.println("Enter your phone number");
        String phonenumber=sc.nextLine();
        obj.setPhonenumber(phonenumber);
        System.out.println("Enter your district name:");
        String district=sc.nextLine();
        obj.setDistrict(district);
       System.out.println("Enter your age");
       int age=sc.nextInt();
       obj.setAge(age);
        System.out.println("------------");
        System.out.println("YOUR BEAUTIFULL NAME IS :: "+obj. getName());
        System.out.println("YOUR VALID EMAIL ID IS  :: "+obj. getEmail());
        System.out.println("YOUR PHONE NUMBER IS :: "+obj. getPhonenumber());
        System.out.println("YOUR DISTRICT NAME IS :: "+obj. getDistrict());
        System.out.println("YOUR AGE IS :: "+obj. getAge());
        System.out.println("------------");
                System.out.println("Some health issues are");
                System.out.println("""
                           1) Fever
                           2) Common cold
                           3) Headache
                           4) Abdominal Pain
                           5) Influenza
                           6) Covid 19
                           7) dental
                           8) malaria
                           9) dengu 
                           10) Diarrhea""");
                System.out.println("Enter your choice based on your health issues");
                String eid=KB.readLine();
                ResultSet result=stmt.executeQuery("select * from medicines_details where disease='"+eid+"'");
                while(result.next())
                    {
                        System.out.println("********");
                        System.out.println("YOUR DISEASE :: "+result.getString("disease"));
                        System.out.println("MEDICINE TO BE TAKEN FOR YOUR HEALTH PROBLEM :: "+result.getString("medicine_name"));
                        System.out.println("SYMPTOMS ARE :: "+result.getString("symptoms"));
                        System.out.println("CAN INTAKE FROM AGE :: "+result.getInt("upto_age"));
                        System.out.println("MANUFACTURED DATE :: "+result.getDate("manufacture_date"));
                        System.out.println("EXPIRY DATE :: "+result.getDate("expiry_date"));
                        System.out.println("EXPIRED OR NOT :: "+result.getString("expired_or_not"));
                        System.out.println("DOSE USAGE :: "+result.getInt("dosage")+"mg/ml");
                        System.out.println("BEFORE FOOD :: "+result.getString("after_food"));
                        System.out.println("AFTER FOOD :: "+result.getString("before_food"));
                        System.out.println("SIDE EFFECTS ARE :: "+result.getString("side_effects"));
                        System.out.println("RUPPES :: "+result.getInt("ruppes")+"/-STRIP");
                        System.out.println("********");
                    }   
             }catch (Exception e){
            System.out.println(e);
            System.out.println("Not connected");
        }
           finally {            
                System.out.println("*******");
                System.out.println("""
                                                  .....IF HEALTH IS LOST EVERYTHING IS LOST......
                                                  .....To live a Healthy life eat a healthy food ....
                                                  .....Do the excersie daily.....
                                                  .....Drink more water....
                                                  .....Stay safe stay healthy....""");
                System.out.println("*******");
              }  
        }
     }
    

 
