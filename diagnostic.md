# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  # < Because it helps us keep our data better organized.  We can separate
  # tables by highly specific categories but easily connect them with
  # relationships>
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `start_date`, `end_date`, and `market`.
                  ^***Typo - Was state_date

```sh
  # < This relationship is one-to-many program to students.  Realistically,
  # a student won't be in multiple programs but a program will have many
  # students.  In the Students table, there should be a column called
  #program_id, to make a relationship between the two. >
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
  # The scheme.rb file dictates our active database schema to the rest of our
  # code.  Migrations update the schema file, but the schema file itself is what
  # our code looks at.
  #
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
  # < Your Response Here >
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
  # The Books table will get the foreign key column because authors have many
  # books, and therefore will show up on the books table multiple times.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
  rails g migration AddAuthorToBooks author:references
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
  # < Validates :author, uniqueness: true >
```
