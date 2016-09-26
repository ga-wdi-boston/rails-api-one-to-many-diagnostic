# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
By having relationships in our API, we can then link / make associations between types
of data, allowing us to save time (and code) when we want to access those relationships.
It also lets us set up one to many relationships, which can make our data a little easier
to work with and understand.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  given_name TEXT,
  surname TEXT,
  hometown TEXT,
  nickname TEXT,
  program_id
);

CREATE TABLE programs (
  id SERIAL PRIMARY KEY,
  start_date DATE,
  end_date DATE,
  market TEXT,
);

A program can have many students, and a student belongs_to a program, therefore
the Foreign Key Reference will go in the Student table.
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
The schema file gives us an overview of all of our migrations. If we reset our database,
it will rebuild based on the schema, not the migrations.

However, the migrations are what build the table, and they show the order (and any edits made)
of the process. For the most part, we will always be using our migrations to build / edit tables, and only using the schema for references.
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
     bundle exec rails g migration RemoveAuthorFromBooks author

this will give us a migration file that contains:

class RemoveAuthorFromBooks < ActiveRecord::migration
  def change
    remove_column :books, :author, :string
  end
end
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
The books table will get the foreign key because it is the plurality, or the receiver
of the 'belongs_to' in this relationship. A book belongs_to an author, and an author has_many books.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
     bundle exec rails g migration AddAuthorRefToBooks author:references
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
I imagine it would look something like this, though I\'m not totally sure:

  class Book < ActiveRecord ::Base
  validates :title, uniqueness: true
```
