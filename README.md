# Student Management System

## Overview

This project is a simple Student Management System implemented in Python. It allows users to add, delete, update, and view student information. The system follows SOLID principles, eliminates redundancy (DRY), simplifies the design (KISS), and avoids unnecessary features (YAGNI).

## Features

- Add new students with unique IDs
- Delete students by ID
- Update student information
- View all students

## How to Run

1. **copy code from the code file in the repository** https://github.com/Akutokuraimagen27/Assignment-/blob/main/codes

3. **paste them into the idl**

4. **Run the system**:
    ```bash
    python student_management_system.py
    ``

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

