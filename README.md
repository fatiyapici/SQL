# SQL Practices

## SQL Basics


 1. **Film tablosunda bulunan title ve description sütunlarındaki verileri
    sıralayınız.**

	*SELECT title,description FROM film*
	
 2. **Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.**

	*SELECT * FROM film 
    WHERE (length >= 60 
    AND length <= 75) 
    ORDER BY length*
	
 3. **Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.**

	*SELECT * FROM film 
    WHERE (rental_rate = 0.99 
    AND replacement_cost = 12.99 
    OR replacement_cost = 28.99) 
	ORDER BY replacement_cost*
	 
 4. **Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?**

	*SELECT last_name FROM customer 
    WHERE first_name = 'Mary'*
	 
 5. **Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.**

	*SELECT * FROM film 
    WHERE length < 50 
    AND NOT (rental_rate = 2.99 
    OR rental_rate = 4.99) 
    ORDER BY length*
    
 6. **Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)**
    
    *SELECT * FROM film 
    WHERE replacement_cost 
    BETWEEN 12.99 
    AND 16.99
    ORDER BY replacement_cost*

7. **Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)**

    *SELECT first_name,last_name FROM actor 
    WHERE first_name 
    IN ('Penelope', 'Nick', 'Ed')
    ORDER BY last_name ASC*

8. **Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)**

    *SELECT * FROM film 
    WHERE rental_rate 
    IN (0.99, 2.99, 4.99) 
    AND replacement_cost 
    IN (12.99, 15.99, 28.99)
    ORDER BY rental_rate*

9. **Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.**

    *SELECT * FROM country 
    WHERE country 
    LIKE 'A%a'*

10. **Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.**

    *SELECT * FROM country 
    WHERE country 
    LIKE '______%n'*

11. **Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.**

    *SELECT title FROM film 
    WHERE title 
    LIKE '____%t%'*

12. **Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.**

    *SELECT * FROM film 
    WHERE title 
    LIKE 'C%' 
    AND length > 90 
    AND rental_rate = 2.99 
    ORDER BY length*

13. **Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.**

    *SELECT DISTINCT replacement_cost FROM film 
    ORDER BY replacement_cost*

14. **Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?**

    *SELECT COUNT(DISTINCT replacement_cost) FROM film*

15. **Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?**

    *SELECT COUNT(DISTINCT title) FROM film 
    WHERE title 
    LIKE 'T%' 
    AND rating = 'G'*

16. **Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?**

    *SELECT COUNT(DISTINCT country) FROM country 
    WHERE country 
    LIKE '_____'*

17. **City tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?**

    *SELECT COUNT(city) FROM city 
    WHERE city 
    ILIKE '%R'*

18. **Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.**

    *SELECT * FROM film 
    WHERE title 
    ILIKE '%N' 
    ORDER BY length 
    DESC LIMIT 5*

## SQL Basics II

19. **Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.**

    *SELECT * FROM film 
    WHERE title 
    ILIKE '%N' 
    ORDER BY length 
    LIMIT 5 
    OFFSET 5*

20. **Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.**

    *SELECT * FROM customer 
    WHERE store_id = 1 
    ORDER BY last_name 
    DESC LIMIT 4*

21. **Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?**

    *SELECT AVG(rental_rate) FROM film*

22. **Film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?**

    *SELECT COUNT(title) FROM film 
    WHERE title 
    LIKE 'C%'*

23. **Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?**

    *SELECT length FROM film 
    WHERE rental_rate = 0.99 
    ORDER BY length 
    DESC LIMIT 1*

24. **Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?**

    *SELECT COUNT(DISTINCT replacement_cost) FROM film 
    WHERE length > 150*

25. **Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.**

    *SELECT rating, COUNT(*) AS film FROM film
    GROUP BY rating
    ORDER BY film*

26. **Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.**

    *SELECT replacement_cost, COUNT(*) AS film
    FROM film
    GROUP BY replacement_cost
    HAVING COUNT(*) > 50
    ORDER BY replacement_cost*

27. **Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayıları nelerdir?**

    *SELECT store_id, COUNT(*) AS customer
    FROM customer
    GROUP BY store_id*

28. **City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.**

    *SELECT country_id, COUNT(*) as city_count
    FROM city
    GROUP BY country_id
    ORDER BY city_count DESC
    LIMIT 1*

## Tables

29. **Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.**

    *CREATE TABLE author (
    id int,
    name VARCHAR(50),
    birthday DATE,
    email VARCHAR(100)
    )*

30. **Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.**

    *insert into employee (id, name, email, birthday) values (1, 'Orel', 'ostapels0@zimbio.com', '1901-06-03');
    insert into employee (id, name, email, birthday) values (2, 'Tabbie', 'tismail1@berkeley.edu', '1974-03-18');
    insert into employee (id, name, email, birthday) values (3, 'Clifford', 'cjirik2@google.nl', '2020-07-03') ...*

31. **Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.**

    *UPDATE employee
    SET name = '11111',
	birthday = '1980-01-01',
    email = 'first@first.com'
    WHERE id = 1*

    *UPDATE employee
    SET name = '22222',
	birthday = '1980-01-01',
    email = 'second@second.com'
    WHERE id = 2 ...*

32. **Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.**

    *DELETE FROM employee
    WHERE name = '11111'*
    *DELETE FROM employee
    WHERE name = '22222' ...*

## JOIN STRUCTURES

33. **City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.**

    *SELECT city.city, country.country
    FROM city
    INNER JOIN country 
    ON country.country_id = city.country_id*

34. **Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.**

    *SELECT payment.payment_id, customer.first_name, customer.last_name
    FROM payment
    INNER JOIN customer
    ON payment.customer_id = customer.customer_id*

35. **Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.**

    *SELECT rental.rental_id, customer.first_name, customer.last_name
    FROM rental
    INNER JOIN customer
    ON rental.customer_id = customer.customer_id*

36. **City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.**

    *SELECT city.city, country.country 
    FROM city
    LEFT JOIN country
    ON country.country_id = city.country_id*

37. **Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.**

    *SELECT payment_id, first_name, last_name
    FROM payment
    RIGHT JOIN customer
    ON customer.customer_id = payment.customer_id*

38. **Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.**

    *SELECT rental_id, first_name, last_name
    FROM rental
    FULL JOIN customer
    ON customer.customer_id = rental.customer_id*

39. **Actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.**

    *(SELECT first_name
    FROM actor)
    UNION
    (SELECT first_name
    FROM customer)*

40. **Actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.**

    *(SELECT first_name
    FROM actor)
    INTERSECT
    (SELECT first_name
    FROM customer)*

41. **Actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.**

    *(SELECT first_name
    FROM actor)
    EXCEPT
    (SELECT first_name
    FROM customer)*

42. **39, 40 ve 41. sorguyu tekrar eden veriler için de yapalım.**

    *(SELECT first_name
    FROM actor)
    UNION ALL
    (SELECT first_name
    FROM customer)*

    *(SELECT first_name
    FROM actor)
    INTERSECT ALL
    (SELECT first_name
    FROM customer)*

    *(SELECT first_name
    FROM actor)
    EXCEPT ALL
    (SELECT first_name
    FROM customer)*

43. **Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?**

    *SELECT * FROM film
    WHERE length >
    (SELECT AVG(film.length)
    FROM film)*

44. **Film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?**

    *SELECT * FROM film
    WHERE rental_rate =
    (SELECT MAX(film.rental_rate)
    FROM film)*

45. **Film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.**

    *SELECT * FROM film
    WHERE rental_rate = 
    (SELECT MIN(film.rental_rate) FROM film)
    AND replacement_cost = 
    (SELECT MIN(film.replacement_cost) FROM film)*

46. **Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.**

    *SELECT c.customer_id, c.first_name, c.last_name, c.email, COUNT(p.payment_id) AS transaction_count
    FROM customer c
    JOIN payment p ON c.customer_id = p.customer_id
    GROUP BY c.customer_id, c.first_name, c.last_name, c.email
    ORDER BY transaction_count DESC*

## OVERVIEW

47. **Film tablosundan 'K' karakteri ile başlayan en uzun ve replacenet_cost u en düşük 4 filmi sıralayınız.**

    *SELECT title, length, replacement_cost
    FROM film
    WHERE title LIKE 'K%'
    ORDER BY length DESC, replacement_cost ASC
    LIMIT 3*

48. **Film tablosunda içerisinden en fazla sayıda film bulunduran rating kategorisi hangisidir?**

    *SELECT rating, COUNT(*)
    FROM film
    GROUP BY rating
    ORDER BY COUNT(*) DESC
    LIMIT 1*

49. **Customer tablosunda en çok alışveriş yapan müşterinin adı nedir?**

    *SELECT customer.first_name, customer.last_name, SUM(amount)
    FROM payment
    JOIN customer ON customer.customer_id = payment.customer_id
    GROUP BY customer.first_name, customer.last_name, payment.customer_id
    ORDER BY sum DESC
    LIMIT 1*

50. **Category tablosundan kategori isimlerini ve kategori başına düşen film sayılarını sıralayınız.**

    *SELECT category.name, COUNT(*)
    FROM film
    JOIN film_category ON film_category.film_id = film.film_id 
    JOIN category ON category.category_id = film_category.category_id
    GROUP BY category.name
    ORDER BY category.name*

51. **Film tablosunda isminde en az 4 adet 'e' veya 'E' karakteri bulunan kç tane film vardır?**

    *SELECT COUNT(*) FROM film
    WHERE title ILIKE '%e%e%e%e%'*