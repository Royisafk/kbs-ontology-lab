University Course Ontology

Description
This project represents a simple ontology for a university academic system using Python. The ontology models key academic entities such as students, lecturers, courses, departments, classrooms and the relationships that exist between them.The system demonstrates how ontology concepts can be represented using Python classes and relationships through dictionaries and functions. It allows users to query information about student enrollments, lecturer assignments, departmental courses, course prerequisites and classroom allocations.

class Student:
    def __init__(self, student_id, name, programme, year):
        self.student_id = student_id
        self.name = name
        self.programme = programme
        self.year = year
class Lecturer:
    def __init__(self, lecturer_id, name, specialization):
        self.lecturer_id = lecturer_id
        self.name = name
        self.specialization = specialization
class Course:
    def __init__(self, course_code, title, level):
        self.course_code = course_code
        self.title = title
        self.level = level
class Department:
    def __init__(self, dept_id, name):
        self.dept_id = dept_id
        self.name = name
class Classroom:
    def __init__(self, room_id, building, capacity):
        self.room_id = room_id
        self.building = building
        self.capacity = capacity
student1 = Student("S1", "Mary", "Applied Computer Technology", 2)
student2 = Student("S2", "Brian", "Applied Computer Technology", 3)
student3 = Student("S3", "Linda", "Applied Computer Technology", 4)
student4 = Student("S4", "Kevin", "Information Systems", 2)
student5 = Student("S5", "Grace", "Information Systems", 3)

students = [student1, student2, student3, student4, student5]

lecturer1 = Lecturer("L1", "Dr. Otieno", "Knowledge Based Systems")
lecturer2 = Lecturer("L2", "Dr. Wanjiku", "Database Systems")
lecturer3 = Lecturer("L3", "Mr. Kamau", "Networking")

lecturers = [lecturer1, lecturer2, lecturer3]


dept1 = Department("D1", "Computer Science")
dept2 = Department("D2", "Information Technology")

departments = [dept1, dept2]


room1 = Classroom("CR11", "Main Block", 50)
room2 = Classroom("CR12", "Science Block", 40)
room3 = Classroom("LAB1", "ICT Block", 35)

classrooms = [room1, room2, room3]


course1 = Course("APT3020", "Knowledge Based Systems", 3)
course2 = Course("IST4040", "Database Management", 4)
course3 = Course("APT4040", "Artificial Intelligence", 4)
course4 = Course("NET3010", "Computer Networks", 3)
course5 = Course("WEB2010", "Web Development", 2)

courses = [course1, course2, course3, course4, course5]



enrollments = {
    "Mary": ["APT3020", "IST4040"],
    "Brian": ["APT3020", "NET3010"],
    "Linda": ["APT3020", "APT4040"],
    "Kevin": ["WEB2010"],
    "Grace": ["IST4040", "NET3010"]
}


teaching_assignments = {
    "APT3020": "Dr. Otieno",
    "IST4040": "Dr. Wanjiku",
    "APT4040": "Dr. Otieno",
    "NET3010": "Mr. Kamau",
    "WEB2010": "Dr. Wanjiku"
}


course_departments = {
    "APT3020": "Computer Science",
    "IST4040": "Computer Science",
    "APT4040": "Computer Science",
    "NET3010": "Information Technology",
    "WEB2010": "Information Technology"
}


prerequisites = {
    "APT4040": "APT3020",
    "IST4040": "WEB2010",
    "NET3010": "WEB2010"
}


course_classrooms = {
    "APT3020": "CR101",
    "IST4040": "CR102",
    "APT4040": "LAB1",
    "NET3010": "CR101",
    "WEB2010": "LAB1"
}


completed_courses = {
    "Mary": ["WEB2010"],
    "Brian": ["WEB2010", "APT3020"],
    "Linda": ["WEB2010", "APT3020"],
    "Kevin": [],
    "Grace": ["WEB2010"]
}




def get_student_courses(student_name):
    print(f"\nCourses taken by {student_name}:")
    
  if student_name in enrollments:
        for course in enrollments[student_name]:
            print("-", course)
    else:
        print("Student not found.")



def get_course_lecturer(course_code):
    print(f"\nLecturer teaching {course_code}:")
    
  if course_code in teaching_assignments:
        print("-", teaching_assignments[course_code])
    else:
        print("Course not found.")



def get_department_courses(department_name):
    print(f"\nCourses in {department_name} Department:")
    
  found = False
    
   for course, dept in course_departments.items():
        if dept == department_name:
            print("-", course)
            found = True
    if not found:
      print("No courses found.")



def get_students_in_course(course_code):
    print(f"\nStudents taking {course_code}:")
    
  found = False    
    for student, course_list in enrollments.items():
        if course_code in course_list:
            print("-", student)
            found = True

  if not found:
        print("No students enrolled.")



def can_take_course(student_name, course_code):
    print(f"\nCan {student_name} take {course_code}?")
    
  if course_code not in prerequisites:
        print("Yes. No prerequisite required.")
        return
    required_course = prerequisites[course_code]

  if required_course in completed_courses.get(student_name, []):
        print("Yes. Prerequisite satisfied.")
    else:
        print(f"No. Missing prerequisite: {required_course}")

get_student_courses("Mary")

get_course_lecturer("APT3020")

get_department_courses("Computer Science")

get_students_in_course("APT3020")

can_take_course("Mary", "APT4040")

can_take_course("Brian", "APT4040")




<img width="552" height="526" alt="Screenshot 2026-06-19 170818" src="https://github.com/user-attachments/assets/4ee499de-2a6d-489a-bc26-0ef10afd888b" />




Ontology Concepts
1.Students
Represented by attributes:
Student ID
Name
Programme
Year of study

2. Lecturers
Represented by attributes:
Lecturer ID
Name
Specialization

3. Courses
Represented by attributes:
Course Code
Course Title
Course Level

4. Departments
Represented by attributes:
Department ID
Department Name

5. Classrooms
Represents teaching venues with attributes:
Room ID
Building
Capacity


Relationships
Student Enrolled in Course
Stores the courses that each student is registered for.

Example:
Mary - APT3020, IST4040
Brian - APT3020, NET3010

Lecturer Teaches Course
Assigns lecturers to specific courses.
Example:
Dr. Otieno - APT3020
Dr. Wanjiku - IST4040

Course Belongs to Department
Links each course to a department.
Example:
APT3020 - Computer Science
WEB2010 - Information Technology

Course Has Prerequisite
Defines prerequisite requirements for advanced courses.
Example:
APT4040 requires APT3020
NET3010 requires WEB2010

Course Taught in Classroom
Assigns classrooms to courses.
Example:
APT3020 - CR101
APT4040 - LAB1

Features
The system provides the following functionality:
View courses taken by a student.
Find the lecturer teaching a course.
Display all courses in a department.
List students enrolled in a course.
Check whether a student satisfies course prerequisites.

Sample Queries
Get Courses Taken by a Student
get_student_courses("Mary")

Get Lecturer Teaching a Course
get_course_lecturer("APT3020")

Get Courses in a Department
get_department_courses("Computer Science")

Get Students Enrolled in a Course
get_students_in_course("APT3020")


Check Course Eligibility
can_take_course("Mary", "APT4040")


How to Run
1. Ensure Python 3 is installed on your computer.
2. Save the code as ontology_lab.py
3. Open a terminal 
4. Navigate to the project folder.
5. Run the program using python ontology_lab.py

Author
Roy Kinyanjui
