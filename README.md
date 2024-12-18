Q 1. Create a class in which accept name, sir-name & display it.

import java.util.Scanner;
class Person {
String name;
String surname;
void acceptDetails() {
Scanner sc = new Scanner(System.in);
System.out.print("Enter Name: ");
name = sc.nextLine();
System.out.print("Enter Surname: ");
surname = sc.nextLine();
}
void displayDetails() {
System.out.println("Name: " + name);
System.out.println("Surname: " + surname);
}
}
public class Q1 {
public static void main(String[] args) {
Person p = new Person();
p.acceptDetails();
p.displayDetails() }
}


Q 2. Accept the Roll no, Name, City connect to the database & store it.
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.util.Scanner;
public class Q2 {
public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
System.out.print("Enter Roll No: ");
int rollNo = sc.nextInt();
sc.nextLine(); // Consume newline
System.out.print("Enter Name: ");
String name = sc.nextLine();
System.out.print("Enter City: ");
String city = sc.nextLine();
try {
Connection con =
DriverManager.getConnection("jdbc:mysql://localhost:3306/mydatabase", "root",
"password");
String query = "INSERT INTO students (roll_no, name, city) VALUES (?, ?, ?)";
PreparedStatement pstmt = con.prepareStatement(query);
pstmt.setInt(1, rollNo);
pstmt.setString(2, name);
pstmt.setString(3, city);
pstmt.executeUpdate();
System.out.println("Data Stored Successfully.");
con.close();
} catch (Exception e) {
System.out.println(e);
}
}
}


Q 3. Accept the 1no in base class display positive or negative number in child class
import java.util.Scanner;
class Base {
int number;
void acceptNumber() {
Scanner sc = new Scanner(System.in);
System.out.print("Enter a number: ");
number = sc.nextInt();
}
}
class Child extends Base {
void displayNumberType() {
if (number > 0) {
System.out.println("The number is Positive.");
} else if (number < 0) {
System.out.println("The number is Negative.");
} else {
System.out.println("The number is Zero.");
}
}
}
public class Q3 {
public static void main(String[] args) {
Child c = new Child();
c.acceptNumber();
c.displayNumberType();
}
}


Q 4. Accept the 2no in base class display positive or negative number in child class
import java.util.Scanner;
class Base1 {
int number1;
void acceptNumber1() {
Scanner sc = new Scanner(System.in);
System.out.print("Enter the first number: ");
number1 = sc.nextInt();
}
}
class Base2 {
int number2;
void acceptNumber2() {
Scanner sc = new Scanner(System.in);
System.out.print("Enter the second number: ");
number2 = sc.nextInt();
}
}
class ChildClass extends Base1 {
Base2 b2 = new Base2();
void displayNumbersType() {
acceptNumber1();
b2.acceptNumber2();
System.out.println("First number is: " + (number1 >= 0 ? "Positive" : "Negative"));
System.out.println("Second number is: " + (b2.number2 >= 0 ? "Positive" :
"Negative"));
}
}
public class Q4 {
public static void main(String[] args) {
ChildClass c = new ChildClass();
c.displayNumbersType();
}
}


Q 5. Pi = 3.14 const. in interface calculate area of circle in which accept radius.
import java.util.Scanner;
interface Circle {
double PI = 3.14;
void calculateArea();
}
class CircleImpl implements Circle {
double radius;
public void calculateArea() {
Scanner sc = new Scanner(System.in);
System.out.print("Enter radius of the circle: ");
radius = sc.nextDouble();
double area = PI * radius * radius;
System.out.println("The area of the circle is: " + area);
}
}
public class Q5 {
public static void main(String[] args) {
CircleImpl circle = new CircleImpl();
circle.calculateArea();
}
}


Q 6. Accept the length, breadth & show area of rectangle.
import java.util.Scanner;
class Rectangle {
int length, breadth;
void acceptDetails() {
Scanner sc = new Scanner(System.in);
System.out.print("Enter Length: ");
length = sc.nextInt();
System.out.print("Enter Breadth: ");
breadth = sc.nextInt();
}
void calculateArea() {
int area = length * breadth;
System.out.println("The Area of the Rectangle is: " + area);
}
}
public class Q6 {
public static void main(String[] args) {
Rectangle rect = new Rectangle();
rect.acceptDetails();
rect.calculateArea();
}
}


Q 7. Accept the 1no in base class ,2nd no in another base class display the multiplication of
that no in child class.
class BaseA {
int number1;
void acceptNumber1(int n) {
number1 = n;
}
}
class BaseB {
int number2;
void acceptNumber2(int n) {
number2 = n;
}
}
class ChildClass extends BaseA {
BaseB b2 = new BaseB();
void displayMultiplication() {
System.out.println("Multiplication of " + number1 + " and " + b2.number2 + " is: " +
(number1 * b2.number2));
}
}
public class Q7 {
public static void main(String[] args) {
ChildClass child = new ChildClass();
child.acceptNumber1(5); // Example number 1
child.b2.acceptNumber2(3); // Example number 2
child.displayMultiplication();
}
}


Q 8. Accept the 2 integer no. & 2 float no. calculate multiplication of integer no. & addition
of float no. (Use method overloading).
class Calculator {
void calculate(int a, int b) {
System.out.println("Multiplication of Integers: " + (a * b));
}
void calculate(float x, float y) {
System.out.println("Addition of Floats: " + (x + y));
}
}
public class Q8 {
public static void main(String[] args) {
Calculator calc = new Calculator();
calc.calculate(4, 5); // Integers
calc.calculate(3.2f, 4.8f); // Floats
}
}


Q 9. By the use of swing framework accept the EmpId, Name, Salary & show it.
import javax.swing.*;
public class Q9 {
public static void main(String[] args) {
JFrame frame = new JFrame("Employee Details");
JTextField empIdField = new JTextField();
JTextField nameField = new JTextField();
JTextField salaryField = new JTextField();
empIdField.setBounds(150, 50, 150, 20);
nameField.setBounds(150, 80, 150, 20);
salaryField.setBounds(150, 110, 150, 20);
JLabel empIdLabel = new JLabel("Emp ID:");
JLabel nameLabel = new JLabel("Name:");
JLabel salaryLabel = new JLabel("Salary:");
empIdLabel.setBounds(50, 50, 100, 20);
nameLabel.setBounds(50, 80, 100, 20);
salaryLabel.setBounds(50, 110, 100, 20);
JButton submitButton = new JButton("Submit");
submitButton.setBounds(150, 150, 100, 30);
submitButton.addActionListener(e -> {
String empId = empIdField.getText();
String name = nameField.getText();
String salary = salaryField.getText();
JOptionPane.showMessageDialog(null, "Emp ID: " + empId + "\nName: " + name +
"\nSalary: " + salary);
});
frame.add(empIdField);
frame.add(nameField);
frame.add(salaryField);
frame.add(empIdLabel);
frame.add(nameLabel);
frame.add(salaryLabel);
frame.add(submitButton);
frame.setSize(400, 300);
frame.setLayout(null);
frame.setVisible(true);
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
}
}


Q 10. By the use of AWT, Swing accept the Name, Roll no, City & store in Wamp Server
(MySQL).
import java.awt.*;
import java.awt.event.*;
import java.sql.*;
public class Q10 {
public static void main(String[] args) {
Frame frame = new Frame("Student Form");
Label nameLabel = new Label("Name:");
Label rollLabel = new Label("Roll No:");
Label cityLabel = new Label("City:");
TextField nameField = new TextField();
TextField rollField = new TextField();
TextField cityField = new TextField();
Button submitButton = new Button("Submit");
// Positioning Components
nameLabel.setBounds(50, 50, 80, 30);
nameField.setBounds(150, 50, 150, 30);
rollLabel.setBounds(50, 100, 80, 30);
rollField.setBounds(150, 100, 150, 30);
cityLabel.setBounds(50, 150, 80, 30);
cityField.setBounds(150, 150, 150, 30);
submitButton.setBounds(150, 200, 80, 30);
frame.add(nameLabel);
frame.add(nameField);
frame.add(rollLabel);
frame.add(rollField);
frame.add(cityLabel);
frame.add(cityField);
frame.add(submitButton);
frame.setSize(400, 300);
frame.setLayout(null);
frame.setVisible(true);
submitButton.addActionListener(new ActionListener() {
public void actionPerformed(ActionEvent e) {
String name = nameField.getText();
int rollNo = Integer.parseInt(rollField.getText());
String city = cityField.getText();
try {
Connection con =
DriverManager.getConnection("jdbc:mysql://localhost:3306/mydatabase", "root",
"password");
PreparedStatement stmt = con.prepareStatement("INSERT INTO students
(roll_no, name, city) VALUES (?, ?, ?)");
stmt.setInt(1, rollNo);
stmt.setString(2, name);
stmt.setString(3, city);
stmt.executeUpdate();
con.close();
System.out.println("Data Stored Successfully!");
} catch (Exception ex) {
System.out.println(ex);
}
}
});
frame.addWindowListener(new WindowAdapter() {
public void windowClosing(WindowEvent we) {
System.exit(0);
}
});
}
}


Q 11. By the use of Spring Framework create registration form of employee & store it.
public class Employee {
private int id;
private String name;
private String email;
// Getters and Setters
}
import org.springframework.web.bind.annotation.*;
@RestController
@RequestMapping("/employee")
public class EmployeeController {
@PostMapping("/register")
public String registerEmployee(@RequestBody Employee emp) {
return "Employee Registered: " + emp.getName();
}
}
@SpringBootApplication
public class Q11Application {
public static void main(String[] args) {
SpringApplication.run(Q11Application.class, args);
}
}


Q 12. By the use of spring boot framework accept the roll no, Name, Password & store in
Wamp Server (MySQL).
public class Student {
private int rollNo;
private String name;
private String password;
// Getters and Setters
}
@RestController
@RequestMapping("/student")
public class StudentController {
@PostMapping("/store")
public String storeStudent(@RequestBody Student student) {
// Logic to save data to DB
return "Student Data Stored Successfully: " + student.getName();
}
}


Q 13. By the use of Spring Boot framework store the employee data in Wamp server the
field name is EmpId, Name, Salary.
public class Employee {
private String empId;
private String name;
private double salary;
// Getters and Setters
}
@RestController
@RequestMapping("/employee")
public class EmployeeController {
@PostMapping("/store")
public String storeEmployee(@RequestBody Employee emp) {
// Logic to save employee to WAMP server
return "Employee Data Saved: " + emp.getName();
}
}


Q 14. By the use of AWT ,Swing accept the CustName ,CustNo & store in JDBC connectivity.
CREATE TABLE customers (
cust_no INT PRIMARY KEY,
cust_name VARCHAR(50)
);
import java.awt.*;
import java.awt.event.*;
import java.sql.*;
public class Q14 {
public static void main(String[] args) {
Frame frame = new Frame("Customer Form");
// Labels
Label custNoLabel = new Label("Customer No:");
Label custNameLabel = new Label("Customer Name:");
// TextFields
TextField custNoField = new TextField();
TextField custNameField = new TextField();
// Button
Button submitButton = new Button("Submit");
// Positioning Components
custNoLabel.setBounds(50, 50, 100, 30);
custNoField.setBounds(200, 50, 150, 30);
custNameLabel.setBounds(50, 100, 100, 30);
custNameField.setBounds(200, 100, 150, 30);
submitButton.setBounds(150, 150, 100, 30);
// Adding Components
frame.add(custNoLabel);
frame.add(custNoField);
frame.add(custNameLabel);
frame.add(custNameField);
frame.add(submitButton);
frame.setSize(400, 250);
frame.setLayout(null);
frame.setVisible(true);
// Action Listener for Submit Button
submitButton.addActionListener(new ActionListener() {
public void actionPerformed(ActionEvent e) {
int custNo = Integer.parseInt(custNoField.getText());
String custName = custNameField.getText();
try {
// JDBC Connection
Connection con =
DriverManager.getConnection("jdbc:mysql://localhost:3306/customerdb", "root",
"password");
String query = "INSERT INTO customers (cust_no, cust_name) VALUES (?, ?)";
PreparedStatement pstmt = con.prepareStatement(query);
pstmt.setInt(1, custNo);
pstmt.setString(2, custName);
int result = pstmt.executeUpdate();
if (result > 0) {
System.out.println("Customer Data Inserted Successfully!");
custNoField.setText("");
custNameField.setText("");
} else {
System.out.println("Insertion Failed!");
}
con.close();
} catch (Exception ex) {
System.out.println("Error: " + ex.getMessage());
}
}
});
// Window Close Event
frame.addWindowListener(new WindowAdapter() {
public void windowClosing(WindowEvent we) {
System.exit(0);
}
});
}
}


Q 15. By the use of AWT, Swing accept the Mobile ID, Mobile Name , Price & store it.
import javax.swing.*;
import java.awt.event.*;
public class Q15 {
public static void main(String[] args) {
JFrame frame = new JFrame("Mobile Data");
JLabel idLabel = new JLabel("Mobile ID:");
JLabel nameLabel = new JLabel("Mobile Name:");
JLabel priceLabel = new JLabel("Price:");
JTextField idField = new JTextField();
JTextField nameField = new JTextField();
JTextField priceField = new JTextField();
JButton submitButton = new JButton("Submit");
idLabel.setBounds(50, 50, 100, 20);
idField.setBounds(150, 50, 150, 20);
nameLabel.setBounds(50, 100, 100, 20);
nameField.setBounds(150, 100, 150, 20);
priceLabel.setBounds(50, 150, 100, 20);
priceField.setBounds(150, 150, 150, 20);
submitButton.setBounds(150, 200, 100, 30);
frame.add(idLabel);
frame.add(idField);
frame.add(nameLabel);
frame.add(nameField);
frame.add(priceLabel);
frame.add(priceField);
frame.add(submitButton);
submitButton.addActionListener(e -> {
String id = idField.getText();
String name = nameField.getText();
String price = priceField.getText();
JOptionPane.showMessageDialog(null, "Mobile ID: " + id + "\nName: " + name +
"\nPrice: " + price);
});
frame.setSize(400, 300);
frame.setLayout(null);
frame.setVisible(true);
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
}
}


Q 16. By the use of AWT, Swing accept the Mobile ID, Mobile Name , Price & store it using
Spring boot.
public class Mobile {
private String id;
private String name;
private double price;
// Getters and Setters
}
@RestController
@RequestMapping("/mobile")
public class MobileController {
@PostMapping("/store")
public String storeMobile(@RequestBody Mobile mobile) {
return "Mobile Data Stored Successfully: " + mobile.getName();
}
}
@SpringBootApplication
public class Q16Application {
public static void main(String[] args) {
SpringApplication.run(Q16Application.class, args);
}
}
