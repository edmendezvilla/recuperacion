
### 1. Crear script DDL
- Sentencia:
```
CREATE TABLE Students (
    student_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    birth_date DATE NOT NULL
);

CREATE TABLE Courses (
    course_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT
);

CREATE TABLE Enrollments (
    enrollment_id SERIAL PRIMARY KEY,
    student_id INT NOT NULL,
    course_id INT NOT NULL,
    enrollment_date DATE NOT NULL,
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);
```

- Captura

<img src="![alt text](image.png)" width="500"/>

### 2. Poblar con datos
---
- Sentencia:
```
INSERT INTO Students (name, email, birth_date) VALUES
('John Smith', 'john.smith@example.com', '2005-04-23'),
('Maria Lopez', 'maria.lopez@example.com', '2006-07-15'),
('Carlos Ruiz', 'carlos.ruiz@example.com', '2007-01-30'),
('Anna Brown', 'anna.brown@example.com', '2006-12-01'),
('Peter Davis', 'peter.davis@example.com', '2005-06-17');


INSERT INTO Courses (name, description) VALUES
('Mathematics', 'Basic mathematics course'),
('Science', 'General science course'),
('History', 'World history course'),
('English', 'English language and literature'),
('Physical Education', 'Physical education and sports');


INSERT INTO Enrollments (student_id, course_id, enrollment_date) VALUES
(1, 1, '2023-09-01'),
(1, 2, '2023-09-01'),
(2, 3, '2023-09-02'),
(3, 1, '2023-09-03'),
(4, 4, '2023-09-04'),
(5, 5, '2023-09-05');
```

- Captura

<img src="![alt text](image-1.png)" alt="drawing0" width="500"/>

### 3. Crear una vista con las 3 tablas
---
- Sentencia:
```
CREATE VIEW EnrollmentView AS
SELECT
    s.student_id,
    s.name AS student_name,
    s.email,
    s.birth_date,
    c.course_id,
    c.name AS course_name,
    c.description,
    e.enrollment_date
FROM
    Enrollments e
JOIN
    Students s ON e.student_id = s.student_id
JOIN
    Courses c ON e.course_id = c.course_id;
```

- Captura

<img src="![alt text](image-2.png)" alt="drawing0" width="500"/>
