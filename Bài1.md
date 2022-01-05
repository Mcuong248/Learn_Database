# Quản lý sinh viên

## Tạo DATABASE
```sql
CREATE DATABASE student
```
## Tạo bảng
```sql
CREATE TABLE subject(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL
)
```

```sql
CREATE TABLE teacher(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    email TEXT NOT NULL,
    mobile VARCHAR(11) NOT NULL,
    address TEXT NOT NULL
)
```

```sql
CREATE TABLE class(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    id_teacher INT NOT NULL,
    FOREIGN KEY (id_teacher) REFERENCES teacher(id)
)
```

```sql
CREATE TABLE student(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    birthday DATE NOT NULL,
    address TEXT NOT NULL,
    mobile VARCHAR(11) NOT NULL,
    email TEXT NOT NULL,
    id_class INT NOT NULL,
    FOREIGN KEY (id_class) REFERENCES class(id)
)
```

```sql
CREATE TABLE point(
	id INT PRIMARY KEY AUTO_INCREMENT,
    id_subject INT NOT NULL,
    id_student INT NOT NULL,
    FOREIGN KEY (id_subject) REFERENCES subject(id),
    FOREIGN KEY (id_student) REFERENCES student(id),
    point FLOAT NOT NULL
)
```