# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  To show the kind of relationship that multiple tables in our database has. For instance, an Author "has_many" Books. While Books "belongs_to" an Author. Creating the link between the two tables allows you to easily query both at the same time.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
  Student: given_name, surname, hometown, nickname.
  Program: start_date, end_date, market.

  A program would have many students, and a student would belong to a single program.

```

1.  For the above example, what needs to be added to the Model files?

```rb
class Student < ActiveRecord::Base
  belongs_to :program
end
```

```rb
class Program < ActiveRecord::Base
  has_many :students
end
```

1.  What is the purpose of our `schema.rb` file? How does it differ from a migration?

```sh
  The schema.rb file shows a representation or overview of the current state of the database.
  A migration, on the other hand, is a specific change to the database schema. For instance,
  adding a column, removing a column, etc.
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
  bundle exec rails g migration RemoveAuthorFromBooks author
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
  The Books table gets a foreign key of "author_id" because books have the
  plurality in the relationship. Many different books could have a single author.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
  bundle exec rails g migration AddAuthorReferenceToBooks author:references
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
  In the Book model, add 'uniqueness: true' to the class.
```
