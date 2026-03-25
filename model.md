# 学生选课成绩系统表结构

## 学生表（student）
| 字段名     | 数据类型 | 约束          | 说明       |
|------------|----------|---------------|------------|
| student_id | INT      | PRIMARY KEY, NOT NULL | 学号（主键） |
| name       | VARCHAR(20) | NOT NULL   | 姓名       |
| gender     | VARCHAR(2) |           | 性别       |
| age        | INT      |               | 年龄       |

## 教师表（teacher）
| 字段名     | 数据类型 | 约束          | 说明       |
|------------|----------|---------------|------------|
| teacher_id | INT      | PRIMARY KEY, NOT NULL | 教师号（主键） |
| name       | VARCHAR(20) | NOT NULL   | 姓名       |
| title      | VARCHAR(20) |           | 职称       |

## 课程表（course）
| 字段名     | 数据类型 | 约束          | 说明       |
|------------|----------|---------------|------------|
| course_id  | INT      | PRIMARY KEY, NOT NULL | 课程号（主键） |
| course_name| VARCHAR(50) | NOT NULL   | 课程名     |
| credit     | DECIMAL(3,1) | NOT NULL | 学分       |
| teacher_id | INT      | FOREIGN KEY REFERENCES teacher(teacher_id) | 授课教师号 |

## 选课成绩表（score）
| 字段名     | 数据类型 | 约束          | 说明       |
|------------|----------|---------------|------------|
| id         | INT      | PRIMARY KEY, AUTO_INCREMENT | 记录ID（主键） |
| student_id | INT      | FOREIGN KEY REFERENCES student(student_id), NOT NULL | 关联学生表 |
| course_id  | INT      | FOREIGN KEY REFERENCES course(course_id), NOT NULL | 关联课程表 |
| score      | DECIMAL(5,1) | NOT NULL | 成绩（0-100） |