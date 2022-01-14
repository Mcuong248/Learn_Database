#### 1 Lấy ra thông tin các diễn viễn đóng phim ACADEMY DINOSAUR
```sql
SELECT film.title, actor.first_name, actor.last_name
FROM film
JOIN film_actor ON film.film_id = film_actor.film_id
JOIN actor ON film_actor.actor_id = actor.actor_id
WHERE title = 'ACADEMY DINOSAUR'
```

#### 2 Lấy ra title, description, release_year, length, rating của các bộ phim có rating là G, đếm xem mỗi phim có bao nhiêu diễn viên tham gia
```sql
SELECT film.film_id, film.title, film.description, film.release_year, film.rating, COUNT(actor.actor_id)
FROM film
JOIN film_actor ON film.film_id = film_actor.film_id
JOIN actor ON film_actor.actor_id = actor.actor_id
WHERE rating = 'G'
GROUP BY film.film_id
```

#### 3 Tính trung bình cộng rental_rate của các phim có CHRISTIAN GABLE tham gia
```sql
SELECT AVG(film.rental_rate) AS TBC
FROM film
JOIN film_actor ON film.film_id = film_actor.film_id
JOIN actor ON film_actor.actor_id = actor.actor_id
WHERE actor.first_name = 'CHRISTIAN' AND actor.last_name = 'GABLE'
```