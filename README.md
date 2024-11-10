# python_class.py
# 基类 Person
class Person_t:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        return f"姓名：{self.name}, 年龄：{self.age}"

# 子类 Teacher
class Teacher_t(Person_t):
    def __init__(self, name, age, subject):
        super().__init__(name, age)
        self.subject = subject

    def introduce(self):
        return f"{super().introduce()}, 教授科目：{self.subject}"

# 子类 Student
class Student_t(Person_t):
    def __init__(self, name, age, grade):
        super().__init__(name, age)
        self.grade = grade

    def introduce(self):
        return f"{super().introduce()}, 年级：{self.grade}"

# 课程类 Course
class Course_t:
    def __init__(self, course_name, teacher):
        self.course_name = course_name
        self.teacher = teacher
        self.students = []

    def add_Student(self, student):
        if student not in self.students:
            self.students.append(student)
            print(f"{student.name} 已被添加到课程 {self.course_name} 中。")

    def remove_Student(self, student):
        if student in self.students:
            self.students.remove(student)
            print(f"{student.name} 已从课程 {self.course_name} 中移除。")

    def show_Course_Info(self):
        print(f"课程名称：{self.course_name}")
        print(f"授课教师：{self.teacher.introduce()}")
        print("选修学生列表：")
        if self.students:
            for student in self.students:
                print(f" - {student.introduce()}")
        else:
            print("暂无学生选修此课程。")

# 主程序
if __name__ == "__main__":
    # 创建教师
    teacher1 = Teacher_t("张老师", 40, "数学")
    teacher2 = Teacher_t("李老师", 35, "英语")

    # 创建课程
    course1 = Course_t("高等数学", teacher1)
    course2 = Course_t("基础英语", teacher2)

    # 创建学生
    student1 = Student_t("小王", 18, "大一")
    student2 = Student_t("小李", 19, "大二")
    student3 = Student_t("小张", 20, "大三")

    # 添加学生到课程
    course1.add_Student(student1)
    course1.add_Student(student2)
    course2.add_Student(student3)
    
     # 展示未修改前的课程信息
    print("\n课程1的信息：")
    course1.show_Course_Info()
    
    print("\n课程2的信息：")
    course2.show_Course_Info()

    # 移除学生
    course1.remove_Student(student2)

    # 展示修改后的课程信息
    print("\n课程1的信息：")
    course1.show_Course_Info()
    
    print("\n课程2的信息：")
    course2.show_Course_Info()