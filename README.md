# Eman-pratice
"A repository to practice GitHub basics."
#include <iostream>
#include <string>
using namespace std;

// Base Class: Person
class Person {
protected:
    string name;
    int age;
public:
    Person(string n, int a) : name(n), age(a) {}
    void displayPersonInfo() {
        cout << "Name: " << name << "\nAge: " << age << endl;
    }
};

// Base Class: Department
class Department {
protected:
    string departmentName;
public:
    Department(string dept) : departmentName(dept) {}
    void displayDepartmentInfo() {
        cout << "Department: " << departmentName << endl;
    }
};

// Derived Class: Teacher (Multiple Inheritance from Person and Department)
class Teacher : public Person, public Department {
protected:
    string employeeID;
    string subject;
public:
    Teacher(string n, int a, string id, string sub, string dept) 
        : Person(n, a), Department(dept), employeeID(id), subject(sub) {}
    void displayTeacherInfo() {
        displayPersonInfo();
        displayDepartmentInfo();
        cout << "Employee ID: " << employeeID << "\nSubject: " << subject << endl;
    }
};

// Derived Class: Student (inherits from Person)
class Student : public Person {
protected:
    string studentID;
    string grade;
public:
    Student(string n, int a, string id, string g) 
        : Person(n, a), studentID(id), grade(g) {}
    void displayStudentInfo() {
        displayPersonInfo();
        cout << "Student ID: " << studentID << "\nGrade: " << grade << endl;
    }
};

// Multilevel Derived Class: HeadStudent (inherits from Student)
class HeadStudent : public Student {
private:
    string responsibility;
public:
    HeadStudent(string n, int a, string id, string g, string r) 
        : Student(n, a, id, g), responsibility(r) {}
    void displayHeadStudentInfo() {
        displayStudentInfo();
        cout << "Responsibility: " << responsibility << endl;
    }
};

// Main Function
int main() {
    // Creating a Teacher object
    Teacher teacher("Mr. John", 45, "T123", "Physics", "Science");
    cout << "Teacher Information:\n";
    teacher.displayTeacherInfo();

    cout << "\n";

    // Creating a Student object
    Student student("Alice", 16, "S456", "10th");
    cout << "Student Information:\n";
    student.displayStudentInfo();

    cout << "\n";

    // Creating a HeadStudent object
    HeadStudent headStudent("Bob", 17, "S789", "12th", "School Captain");
    cout << "Head Student Information:\n";
    headStudent.displayHeadStudentInfo();

    return 0;
}