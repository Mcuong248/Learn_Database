## Quản lý quán coffee
### Tạo Database
```sql
CREATE DATABASE Cafe_Shop
```

### Tạo bảng
```sql
CREATE TABLE staff(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    birthday DATE,
    address VARCHAR(200),
    email VARCHAR(200),
    mobile VARCHAR(11)
)
```

```sql
CREATE TABLE category(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL
)
```

```sql
CREATE TABLE product(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30),
    price FLOAT NOT NULL,
    number_of_buyers INT NOT NULL,
    description TEXT NOT NULL,
    image VARCHAR(30),
    id_category INT NOT NULL,
    FOREIGN KEY (id_category) REFERENCES category(id)
)
```

```sql
CREATE TABLE customer(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30),
    birthday DATE,
    mobile VARCHAR(11),
    email VARCHAR(50),
    address VARCHAR(30) 
)
```

```sql
CREATE TABLE cart(
	id INT PRIMARY KEY AUTO_INCREMENT,
    id_customer INT NOT NULL,
    FOREIGN KEY (id_customer) REFERENCES customer(id)
)
```

```sql
CREATE TABLE cart_details(
	id_cart INT NOT NULL,
    FOREIGN KEY (id_cart) REFERENCES cart(id),
    id_product INT NOT NULL,
    FOREIGN KEY (id_product) REFERENCES product(id),
    quantily INT NOT NULL
)
```

```sql
CREATE TABLE orders(
	id INT PRIMARY KEY AUTO_INCREMENT,
    id_staff INT NOT NULL,
    FOREIGN KEY (id_staff) REFERENCES staff(id),
    id_customer INT NOT NULL,
    FOREIGN KEY (id_customer) REFERENCES customer(id),
    id_voucher INT NOT NULL,
    FOREIGN KEY (id_voucher) REFERENCES voucher(id),
    total_price FLOAT NOT NULL,
    order_date DATE,
    status VARCHAR(30),
    note VARCHAR(1000)
)
```

```sql
CREATE TABLE voucher(
	id INT PRIMARY KEY AUTO_INCREMENT,
    discount_code VARCHAR(30),
    description TEXT NOT NULL,
    discout BIGINT
)
```

```sql
CREATE TABLE orderdetail(
	id INT PRIMARY KEY AUTO_INCREMENT,
    id_orders INT NOT NULL,
    FOREIGN KEY (id_orders) REFERENCES orders(id),
    id_product INT NOT NULL,
    FOREIGN KEY (id_product) REFERENCES product(id),
    number INT NOT NULL,
    price FLOAT,
    total_price FLOAT
)
```

```sql
CREATE TABLE type(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30),
    id_category INT NOT NULL,
    FOREIGN KEY (id_category) REFERENCES category(id)
)
```

#### Thêm dữ liệu
```sql
insert into staff (id, name, birthday, address, email, mobile) values (1, 'Umberto Beaze', '2021-10-29', 'Purranque', 'ubeaze0@shareasale.com', '6464379913');
insert into staff (id, name, birthday, address, email, mobile) values (2, 'Felipa Prozescky', '2022-01-17', 'Anshun', 'fprozescky1@rambler.ru', '3568783427');
insert into staff (id, name, birthday, address, email, mobile) values (3, 'Vernen Klich', '2021-09-28', 'Lipinki Łużyckie', 'vklich2@soundcloud.com', '9383166857');
insert into staff (id, name, birthday, address, email, mobile) values (4, 'Rosie Sate', '2021-08-28', 'Österbybruk', 'rsate3@mit.edu', '7759585038');
insert into staff (id, name, birthday, address, email, mobile) values (5, 'Malchy Marieton', '2021-12-11', 'Vila Nova Sintra', 'mmarieton4@123-reg.co.uk', '9357209018');
```

```sql
insert into customer (id, name, birthday, mobile, email, address) values (6, 'Saleem Warland', '2021-04-01', '1621617815', 'swarland0@e-recht24.de', 'Cotabato');
insert into customer (id, name, birthday, mobile, email, address) values (7, 'Ahmed Jobin', '2021-04-14', '6586829693', 'ajobin1@creativecommons.org', 'Zlatograd');
insert into customer (id, name, birthday, mobile, email, address) values (8, 'Aigneis McGrory', '2021-04-06', '7555674379', 'amcgrory2@multiply.com', 'Kadudampit');
insert into customer (id, name, birthday, mobile, email, address) values (9, 'Ernaline Beneyto', '2021-10-10', '1517166725', 'ebeneyto3@taobao.com', 'Bellavista');
insert into customer (id, name, birthday, mobile, email, address) values (10, 'Brett Capstick', '2021-03-10', '2078739075', 'bcapstick4@linkedin.com', 'Laoxingchang');
```

```sql
insert into cart (id, id_customer) values (1, 10);
insert into cart (id, id_customer) values (2, 6);
insert into cart (id, id_customer) values (3, 8);
insert into cart (id, id_customer) values (4, 9);
insert into cart (id, id_customer) values (5, 7);
```

```sql
insert into category (id, name) values (1, 'Coffee');
insert into category (id, name) values (2, 'Cà phê máy');
insert into category (id, name) values (3, 'Freezee');
insert into category (id, name) values (4, 'Trà');
insert into category (id, name) values (5, 'Sinh tố');
```

```sql
insert into type (id, name, id_category) values (1, 'Nhỏ, Vừa, Lớn', '1');
insert into type (id, name, id_category) values (2, 'Nhỏ, Vừa, Lớn', '3');
insert into type (id, name, id_category) values (3, 'Nhỏ, Vừa, Lớn', '5');
insert into type (id, name, id_category) values (4, 'Nhỏ, Vừa, Lớn', '4');
insert into type (id, name, id_category) values (5, 'Nhỏ, Vừa, Lớn', '2');
```

```sql
insert into voucher (id, discount_code, description, discout) values (1, '24236-271', 'Got it', 60);
insert into voucher (id, discount_code, description, discout) values (2, '0132-0215', 'Got it', 33);
insert into voucher (id, discount_code, description, discout) values (3, '36987-2942', 'Got it', 69);
insert into voucher (id, discount_code, description, discout) values (4, '52685-464', 'Got it', 77);
insert into voucher (id, discount_code, description, discout) values (5, '62670-4821', 'Got it', 60);
```

```sql
insert into orders (id, id_staff, id_customer, id_voucher, total_price, order_date, status, note) values (1, 3, 10, 2, 58, '2021-07-24', 19, 71);
insert into orders (id, id_staff, id_customer, id_voucher, total_price, order_date, status, note) values (2, 5, 8, 5, 59, '2021-07-12', 49, 24);
insert into orders (id, id_staff, id_customer, id_voucher, total_price, order_date, status, note) values (3, 5, 9, 3, 65, '2022-01-20', 92, 44);
insert into orders (id, id_staff, id_customer, id_voucher, total_price, order_date, status, note) values (4, 5, 7, 2, 44, '2021-10-15', 29, 71);
insert into orders (id, id_staff, id_customer, id_voucher, total_price, order_date, status, note) values (5, 2, 10, 4, 66, '2021-12-06', 84, 11);
```

```sql
insert into product (id, name, price, number_of_buyers, description, image, id_category) values (1, 'Cà Phê Sữa', 64, 911, 'Nhỏ, Vừa, Lớn', 'Cà Phê Sữa', 5);
insert into product (id, name, price, number_of_buyers, description, image, id_category) values (2, 'Capuchino', 65, 750, 'Nhỏ, Vừa, Lớn', 'Capuchino', 5);
insert into product (id, name, price, number_of_buyers, description, image, id_category) values (3, 'Freezee Socola', 48, 500, 'Nhỏ, Vừa, Lớn', 'Freezee Socola', 3);
insert into product (id, name, price, number_of_buyers, description, image, id_category) values (4, 'Trà Ô Long', 66, 660, 'Nhỏ, Vừa, Lớn', 'Trà Ô Long', 4);
insert into product (id, name, price, number_of_buyers, description, image, id_category) values (5, 'Sinh tố bơ', 47, 542, 'Nhỏ, Vừa, Lớn', 'Sinh tố bơ', 1);
```

```sql
insert into orderdetail (id, id_orders, id_product, number, price, total_price) values (1, 4, 3, 6, 55, 642);
insert into orderdetail (id, id_orders, id_product, number, price, total_price) values (2, 3, 1, 3, 56, 633);
insert into orderdetail (id, id_orders, id_product, number, price, total_price) values (3, 4, 3, 7, 48, 496);
insert into orderdetail (id, id_orders, id_product, number, price, total_price) values (4, 5, 3, 10, 61, 519);
insert into orderdetail (id, id_orders, id_product, number, price, total_price) values (5, 5, 3, 4, 52, 517);
```

```sql
insert into cart_details (id_cart, id_product, quantily) values (4, 3, 33);
insert into cart_details (id_cart, id_product, quantily) values (2, 3, 59);
insert into cart_details (id_cart, id_product, quantily) values (3, 3, 38);
insert into cart_details (id_cart, id_product, quantily) values (3, 3, 76);
insert into cart_details (id_cart, id_product, quantily) values (4, 2, 52);
```

![](/271792235_256450719942450_260226490657261130_n.png)