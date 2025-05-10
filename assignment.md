# Assignment

## Brief

Create an ERD for each of the following case study question.

## Instructions

Paste the answer as DBML in the answer code section below each question.

### Question 1

Construct an ERD for a social media company whose database includes information about users, their followers, and the posts that they make. Users can follow multiple users and create multiple posts.

Each entity has the following attributes:

- User: id, username, email, created_at
- Post: id, title, body, user_id, status, created_at
- Follows: following_user_id, followed_user_id, created_at

Answer:

```dbml
Table User {
  id integer
  username varchar
  email varchar
  created_at timestamp
}

Table Post {
  id integer
  title varchar
  body text
  user_id integer
  status varchar
  created_at timestamp
}

Table Follows {
  following_user_id integer
  followed_user_id integer
  created_at timestamp
}

Ref user_posts: Post.user_id > User.id // many-to-one
Ref: User.id < Follows.following_user_id 
Ref: User.id < Follows.followed_user_id

```

### Question 2

Construct an ERD for a company that sells books online. The company has a website where customers can browse available books and add them to their shopping carts. Each cart can contain multiple books.

There are 4 entities, think of what attributes each entity should have.

- Customer
- Book
- Cart
- CartItem

Answer:

```dbml
- Customer: id, name, address, phone, email
- Book: id, title, isbn, genre, author, price, book_status, created_at
- Cart: id, customer_id, created_at
- CartItem: book_id, cart_id, quantity, created_at

// Use DBML to define your database structure
// Docs: https://dbml.dbdiagram.io/docs

Table Customer {
  id integer [pk, increment] // mean the id number is a primary key and it increment by 1
  name varchar
  address varchar
  phone integer
  email varchar
}

Table Book {
  id integer [pk, increment] // mean the id number is a primary key and it increment by 1
  title varchar
  isbn interger
  genre varchar
  author varchar
  price decimal(5,2) // means 3.14 or 123.45
  book_status bool
  created_at timestamp
}

Table Cart {
  id integer [pk, increment]
  customer_id integer
  created_at timestamp
}

Table CartItem {
  id integer [pk, increment]
  book_id integer
  cart_id integer
  quantity integer
  created_at timestamp
}

Ref: Customer.id < Cart.customer_id
Ref: Book.id < CartItem.book_id
Ref: Cart.id < CartItem.cart_id

//https://www.w3schools.com/sql/sql_datatypes.asp

```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
