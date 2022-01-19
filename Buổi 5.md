### Phân tích, thiết kế database cho rạp chiếu phim
# Tạo database
```sql
CREATE DATABASE Cinema
```
#### Tạo bảng 
```sql
CREATE TABLE staff(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    birthday DATE NOT NULL,
    address TEXT NOT NULL,
    email TEXT NOT NULL,
    mobile_number VARCHAR(11)
)
```

```sql
CREATE TABLE users(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    email TEXT NOT NULL,
    password VARCHAR(255),
    token VARCHAR(255),
    mobile VARCHAR(11),
    address TEXT NOT NULL,
    last_logged_at DATETIME,
    create_at TIME,
    update_at TIME
)
```

```sql
CREATE TABLE bookings(
	id INT PRIMARY KEY AUTO_INCREMENT,
    users_id INT NOT NULL,
    FOREIGN KEY (users_id) REFERENCES users(id),
    create_at TIME,
    update_at TIME
)
```

```sql
CREATE TABLE films(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    actor TEXT NOT NULL,
    producer TEXT NOT NULL,
    director TEXT NOT NULL,
    duration INT NOT NULL,
    descrilbe TEXT NOT NULL,
    country TEXT NOT NULL,
    create_at TIME,
    update_at TIME
)
```

```sql
CREATE TABLE comments(
	id INT PRIMARY KEY AUTO_INCREMENT,
    users_id INT NOT NULL,
    FOREIGN KEY (users_id) REFERENCES users(id),
    films_id INT NOT NULL,
    FOREIGN KEY (films_id) REFERENCES films(id),
    content TEXT NOT NULL,
    create_at TIME,
    update_at TIME
)
```

```sql
CREATE TABLE ratings(
	id INT PRIMARY KEY AUTO_INCREMENT,
    users_id INT NOT NULL,
    FOREIGN KEY (users_id) REFERENCES users(id),
    films_id INT NOT NULL,
    FOREIGN KEY (films_id) REFERENCES films(id),
    rate INT NOT NULL,
    create_at TIME,
    update_at TIME
)
```

```sql
CREATE TABLE categories(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL
)
```

```sql
CREATE TABLE images(
	id INT PRIMARY KEY AUTO_INCREMENT,
    films_id INT NOT NULL,
    FOREIGN KEY (films_id) REFERENCES films(id),
    path TEXT NOT NULL
)
```

```sql
CREATE TABLE categories_film(
	id INT PRIMARY KEY AUTO_INCREMENT,
    categories_id INT NOT NULL,
    FOREIGN KEY (categories_id) REFERENCES categories(id),
    films_id INT NOT NULL,
    FOREIGN KEY (films_id) REFERENCES films(id)
)
```

```sql
CREATE TABLE rooms(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    status ENUM('open', 'close')
)
```

```sql
CREATE TABLE schedules(
	id INT PRIMARY KEY AUTO_INCREMENT,
    films_id INT NOT NULL,
    FOREIGN KEY (films_id) REFERENCES films(id),
    rooms_id INT NOT NULL,
    FOREIGN KEY (rooms_id) REFERENCES rooms(id),
    start_time DATETIME,
    end_time DATETIME 
)
```

```sql
CREATE TABLE tickets(
	id INT PRIMARY KEY AUTO_INCREMENT,
    payment_method TEXT NOT NULL,
    price FLOAT NOT NULL,
    staff_id INT NOT NULL,
    FOREIGN KEY (staff_id) REFERENCES staff(id),
    schedules_id INT NOT NULL,
    FOREIGN KEY (schedules_id) REFERENCES schedules(id),
    type TEXT NOT NULL
)
```

```sql
CREATE TABLE seats(
	id INT PRIMARY KEY AUTO_INCREMENT,
    rooms_id INT NOT NULL,
    FOREIGN KEY (rooms_id) REFERENCES rooms(id),
    name TEXT NOT NULL,
    status ENUM ('still', 'over')
)
```

```sql
CREATE TABLE bookings_detail(
	id INT PRIMARY KEY AUTO_INCREMENT,
    bookings_id INT NOT NULL,
    FOREIGN KEY (bookings_id) REFERENCES bookings(id),
    tickets_id INT NOT NULL,
    FOREIGN KEY (tickets_id) REFERENCES tickets(id),
    seats_id INT NOT NULL,
    FOREIGN KEY (seats_id) REFERENCES seats(id)
)
```

![](Cinema%20Database.png)

### Thêm dữ liệu
```sql
insert into users (id, name, email, password, token, mobile, address, last_logged_at, create_at, update_at) values (null, 'Lorelei Beed', 'lbeed0@wisc.edu', 'QNHXpf', 29, '5587950513', 'Tanjungsari Barat', '2021-03-29', '3:49', '6:35');
```

```sql
insert into films (id, name, actor, producer, director, duration, descrilbe, country, create_at, update_at) values (null, 'Hole, The', 'Alphonse Le Gallo', 'Leandra Lowseley', 'Magdalene Norway', 36, 1, 'Dzhetygara', '9:35', '1:08');
```

```sql
insert into staff (id, name, birthday, address, email, mobile_number) values (null, 'Leupold Cristofalo', '2021-11-02', 'Ostuncalco', 'lcristofalo0@nytimes.com', '7244376581');
```