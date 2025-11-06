CREATE TABLE Email ( 

    email VARCHAR(100) NOT NULL, 

    student_id INT NOT NULL, 

    PRIMARY KEY (student_id, email) 

); 

  

CREATE TABLE Student_Proj ( 

    student_id INT PRIMARY KEY, 

    first_name VARCHAR(50) NOT NULL, 

    last_name VARCHAR(50) NOT NULL, 

    grade_level INT NOT NULL, 

    email VARCHAR(100) UNIQUE NOT NULL 

); 

  

CREATE TABLE Instructor_Proj( 

    instructor_id INT PRIMARY KEY, 

    first_name VARCHAR (50) NOT NULL, 

    last_name VARCHAR(50) NOT NULL, 

    email VARCHAR (100) UNIQUE NOT NULL, 

    specialty VARCHAR(100) 

); 

  

CREATE TABLE Speciality ( 

    speciality VARCHAR(50) PRIMARY KEY, 

    instructor_id INT NOT NULL, 

    FOREIGN KEY (instructor_id) REFERENCES Instructor_Proj(instructor_id) 

); 

  

CREATE TABLE Module ( 

    module_id INT PRIMARY KEY, 

    title VARCHAR(100) NOT NULL, 

    Duration INT NOT NULL 

); 

  

CREATE TABLE Course_Proj ( 

    course_id INT PRIMARY KEY, 

    title VARCHAR(100) NOT NULL, 

    subject VARCHAR(100) NOT NULL, 

    department VARCHAR(100) NOT NULL, 

    module_id INT NOT NULL, 

    instructor_id INT NOT NULL, 

    FOREIGN KEY (module_id) REFERENCES Module(module_id), 

    FOREIGN KEY (instructor_id) REFERENCES Instructor_Proj(instructor_id) 

); 

  

CREATE TABLE Enrolls_In ( 

    progress INT NOT NULL, 

    status VARCHAR(50) NOT NULL, 

    student_id INT NOT NULL, 

    course_id INT NOT NULL, 

    course_date DATE NOT NULL, 

    PRIMARY KEY (student_id, course_id), 

    FOREIGN KEY (student_id) REFERENCES Student_Proj(student_id), 

    FOREIGN KEY (course_id) REFERENCES Course_Proj(course_id) 

); 

  

CREATE TABLE Date_Proj ( 

    course_date DATE Not NULL, 

    course_id INT NOT NULL, 

    student_id INT NOT NULL, 

    PRIMARY KEY (student_id, course_id, course_date), 

    FOREIGN KEY (student_id, course_id) REFERENCES Enrolls_In(student_id, course_id) 

); 

 

CREATE INDEX idx_student_name ON Student_Proj(last_name, first_name); 

 

CREATE INDEX idx_course_search ON Course_Proj(title, subject); 

 

CREATE INDEX idx_enrollment_date ON Enrolls_In(course_date); 

 

CREATE SEQUENCE student_seq START WITH 1 INCREMENT BY 1; 

CREATE SEQUENCE instructor_seq START WITH 1 INCREMENT BY 1; 

INSERT INTO Email(email) 

VALUES('ksmith@gmail.com'); 

INSERT INTO Email(email) 

VALUES('samuelj12@gmail.com'); 

 

INSERT INTO Student_Proj(student_id, first_name, last_name, grade_level, email) 

VALUES(student_seq.NEXTVAL, 'Kevin', 'Smith', 12, 'ksmith@gmail.com'); 

INSERT INTO Student_Proj(student_id, first_name, last_name, grade_level, email) 

VALUES(student_seq.NEXTVAL, 'Sam', 'Jackson', 10, 'samuelj12@gmail.com'); 

 

INSERT INTO Instructor_Proj(instructor_id, first_name, last_name, email, specialty) 

VALUES(instructor_seq.NEXTVAL, 'Allen', 'James', 'allen.james@temple.edu', 'MATH'); 

INSERT INTO Instructor_Proj(instructor_id, first_name, last_name, email, specialty) 

VALUES(instructor_seq.NEXTVAL, 'Andrew', 'Mebane', 'andrew.mebane@temple.edu', 'MATH'); 

INSERT INTO Instructor_Proj(instructor_id, first_name, last_name, email, specialty) 

VALUES (instructor_seq.NEXTVAL, 'Sarah', 'Lee', 'sarah.lee@university.edu', 'Computer Science'); 

 

INSERT INTO Module (module_id, title, Duration)  

VALUES (1, 'Introduction to Programming Concepts', 10); 

  

INSERT INTO Module (module_id, title, Duration)  

VALUES (2, 'Advanced Data Structures', 15); 

  

INSERT INTO Module (module_id, title, Duration)  

VALUES (3, 'Database Fundamentals', 12); 

  

INSERT INTO Module (module_id, title, Duration)  

VALUES (4, 'Operating Systems Basics', 14); 

  

INSERT INTO Module (module_id, title, Duration)  

VALUES (5, 'Network and Security Essentials', 8); 

  

INSERT INTO Course_Proj (course_id, title, subject, department, module_id, instructor_id) 

VALUES (201, 'Introduction to Programming', 'Computer Science', 'CS', 1, 1); 

INSERT INTO Course_Proj (course_id, title, subject, department, module_id, instructor_id) 

VALUES (202, 'Data Structures', 'Computer Science', 'CS', 2, 2); 

INSERT INTO Course_Proj(course_id, title, subject, department, module_id, instructor_id) 

VALUES (203, 'Algorithms and Complexity', 'Computer Science', 'CS', 3, 3);  

 

COMMIT; 

SELECT i.specialty, s.grade_level, COUNT (s.grade_level) AS NumberInGradeLevel FROM student_proj s FULL OUTER JOIN Instructor_Proj i ON (instructor_id = student_id) GROUP BY specialty, grade_level; 

SELECT c.department, AVG(m.duration) AS AverageModuleDuration FROM course_proj c  JOIN module m USING(module_id) GROUP BY c.department; 
