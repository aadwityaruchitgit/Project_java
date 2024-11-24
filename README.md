# Project_java
import java.util.ArrayList;
import java.util.Scanner;

public class StudentRecordSystem {

    // Inner class to represent a student
    static class Student {
        private String name;
        private int rollNumber;
        private double marks;

        // Constructor to initialize student details
        public Student(String name, int rollNumber, double marks) {
            this.name = name;
            this.rollNumber = rollNumber;
            this.marks = marks;
        }

        // Getter and Setter methods
        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }

        public int getRollNumber() {
            return rollNumber;
        }

        public void setRollNumber(int rollNumber) {
            this.rollNumber = rollNumber;
        }

        public double getMarks() {
            return marks;
        }

        public void setMarks(double marks) {
            this.marks = marks;
        }

        // Method to display student details
        public void displayStudentDetails() {
            System.out.println("Name: " + name);
            System.out.println("Roll Number: " + rollNumber);
            System.out.println("Marks: " + marks);
        }
    }

    // ArrayList to store student records
    private ArrayList<Student> studentList = new ArrayList<>();

    // Method to add a student record
    public void addStudent(String name, int rollNumber, double marks) {
        Student student = new Student(name, rollNumber, marks);
        studentList.add(student);
        System.out.println("Student added successfully!");
    }

    // Method to display all student records
    public void displayStudents() {
        if (studentList.isEmpty()) {
            System.out.println("No records found.");
            return;
        }
        System.out.println("Student Records:");
        for (Student student : studentList) {
            student.displayStudentDetails();
            System.out.println("--------------------------");
        }
    }

    // Main method to run the program
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        StudentRecordSystem system = new StudentRecordSystem();
        boolean continueRunning = true;

        while (continueRunning) {
            System.out.println("\nStudent Record System");
            System.out.println("1. Add Student");
            System.out.println("2. Display All Students");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume the leftover newline

            switch (choice) {
                case 1:
                    System.out.print("Enter student name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter roll number: ");
                    int rollNumber = scanner.nextInt();
                    System.out.print("Enter marks: ");
                    double marks = scanner.nextDouble();
                    system.addStudent(name, rollNumber, marks);
                    break;

                case 2:
                    system.displayStudents();
                    break;

                case 3:
                    continueRunning = false;
                    System.out.println("Exiting the system. Goodbye!");
                    break;

                default:
                    System.out.println("Invalid choice! Please try again.");
            }
        }

        scanner.close();
    }
}

