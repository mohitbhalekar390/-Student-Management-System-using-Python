class Student:
    def _init_(self, student_id, name, age, grade):
        self.student_id = student_id
        self.name = name
        self.age = age
        self.grade = grade

    def update_details(self, name=None, age=None, grade=None):
        if name:
            self.name = name
        if age:
            self.age = age
        if grade:
            self.grade = grade

    def _str_(self):
        return f"ID: {self.student_id}, Name: {self.name}, Age: {self.age}, Grade: {self.grade}"


class StudentManagementSystem:
    def _init_(self):
        self.students = {}

    def add_student(self, student_id, name, age, grade):
        if student_id in self.students:
            print(f"Student ID {student_id} already exists!")
        else:
            self.students[student_id] = Student(student_id, name, age, grade)
            print(f"Student {name} added successfully.")

    def view_students(self):
        if not self.students:
            print("No students available.")
        else:
            for student in self.students.values():
                print(student)

    def update_student(self, student_id, name=None, age=None, grade=None):
        if student_id in self.students:
            self.students[student_id].update_details(name, age, grade)
            print(f"Student ID {student_id} updated successfully.")
        else:
            print(f"Student ID {student_id} not found!")

    def delete_student(self, student_id):
        if student_id in self.students:
            del self.students[student_id]
            print(f"Student ID {student_id} deleted successfully.")
        else:
            print(f"Student ID {student_id} not found!")


# Main Program
if _name_ == "_main_":
    system = StudentManagementSystem()

    while True:
        print("\nStudent Management System")
        print("1. Add Student")
        print("2. View Students")
        print("3. Update Student")
        print("4. Delete Student")
        print("5. Exit")
        choice = input("Enter your choice: ")

        if choice == "1":
            student_id = input("Enter Student ID: ")
            name = input("Enter Name: ")
            age = int(input("Enter Age: "))
            grade = input("Enter Grade: ")
            system.add_student(student_id, name, age, grade)

        elif choice == "2":
            system.view_students()

        elif choice == "3":
            student_id = input("Enter Student ID to update: ")
            name = input("Enter new Name (leave blank to skip): ") or None
            age = input("Enter new Age (leave blank to skip): ")
            age = int(age) if age else None
            grade = input("Enter new Grade (leave blank to skip): ") or None
            system.update_student(student_id, name, age, grade)

        elif choice == "4":
            student_id = input("Enter Student ID to delete: ")
            system.delete_student(student_id)

        elif choice == "5":
            print("Exiting the system. Goodbye!")
            break

        else:
            print("Invalid choice! Please try again.")