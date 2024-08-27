# Student Management System

## Overview

This project is a simple Student Management System implemented in Python. It allows users to add, delete, update, and view student information. The system follows SOLID principles, eliminates redundancy (DRY), simplifies the design (KISS), and avoids unnecessary features (YAGNI).

## Features

- Add new students with unique IDs
- Delete students by ID
- Update student information
- View all students

## How to Run

1. **Clone the repository**:
    ```bash
    git clone
    https://github.com/Akutokuraimagen27/Assignment-
    ```

2. **Run the system**:
    ```bash
    python student_management_system.py
    ```

class Student:
    def __init__(self, id, name, age, major):
        # Initialize a new student with ID, name, age, and major
        self.id = id
        self.name = name
        self.age = age
        self.major = major

    def update_student(self, name=None, age=None, major=None):
        # Update student details if provided
        if name:
            self.name = name
        if age:
            self.age = age
        if major:
            self.major = major

class StudentDisplay:
    @staticmethod
    def display_student(student):
        # Display student details
        print(f"ID: {student.id}, Name: {student.name}, Age: {student.age}, Major: {student.major}")

class StudentDatabase:
    def __init__(self):
        # Initialize an empty list to store students
        self.students = []

    def add_student(self, student):
        # Add a new student if the ID is unique
        if any(s.id == student.id for s in self.students):
            print(f"Student with ID {student.id} already exists.")
            return False
        self.students.append(student)
        return True

    def remove_student(self, student_id):
        # Remove a student by ID if found
        for student in self.students:
            if student.id == student_id:
                self.students.remove(student)
                return True
        print(f"Student with ID {student_id} not found.")
        return False

    def get_student(self, student_id):
        # Retrieve a student by ID
        for student in self.students:
            if student.id == student_id:
                return student
        return None

    def display_all_students(self):
        # Display all students in the database
        for student in self.students:
            StudentDisplay.display_student(student)

class StudentManagementSystem:
    def __init__(self, database):
        # Initialize the student management system with a database
        self.database = database

    def add_new_student(self, id, name, age, major):
        # Create and add a new student to the database
        student = Student(id, name, age, major)
        return self.database.add_student(student)

    def delete_student(self, student_id):
        # Delete a student from the database by ID
        return self.database.remove_student(student_id)

    def update_student_info(self, student_id, name=None, age=None, major=None):
        # Update student information if the student is found
        student = self.database.get_student(student_id)
        if student:
            student.update_student(name, age, major)
            return True
        print(f"Student with ID {student_id} not found.")
        return False

    def show_all_students(self):
        # Display all students in the database
        self.database.display_all_students()

def menu():
    # Initialize the student management system with an empty database
    sms = StudentManagementSystem(StudentDatabase())
    while True:
        # Display menu options
        print("\n1. Add Student\n2. Delete Student\n3. Update Student\n4. View All Students\n5. Exit")
        choice = input("Enter your choice: ")
        if choice == '1':
            # Add a new student
            id = input("Enter ID: ")
            name = input("Enter Name: ")
            age = input("Enter Age: ")
            major = input("Enter Major: ")
            sms.add_new_student(id, name, age, major)
        elif choice == '2':
            # Delete a student
            id = input("Enter ID to delete: ")
            sms.delete_student(id)
        elif choice == '3':
            # Update student information
            id = input("Enter ID to update: ")
            name = input("Enter new Name (leave blank to keep current): ")
            age = input("Enter new Age (leave blank to keep current): ")
            major = input("Enter new Major (leave blank to keep current): ")
            sms.update_student_info(id, name, age, major)
        elif choice == '4':
            # View all students
            sms.show_all_students()
        elif choice == '5':
            # Exit the menu
            break
        else:
            print("Invalid choice. Please try again.")

# Run the menu
menu()



3. **Follow the menu options** to add, delete, update, or view students.

## Changes Made

- **Refactored Code**: Improved code structure to follow SOLID principles.
- **Error Handling**: Added error handling for unique ID checks and non-existent student IDs.
- **Separated Concerns**: Moved display logic to a separate `StudentDisplay` class.
- **Menu System**: Implemented a simple text-based menu for user interaction.

## Example Usage

```plaintext
1. Add Student
2. Delete Student
3. Update Student
4. View All Students
5. Exit
Enter your choice: 1
Enter ID: 101
Enter Name: John Doe
Enter Age: 20
Enter Major: Computer Science

