# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  # Realtionships are important to databses because they establish a connection between two separate but related data sets.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
  # the Students table would have a table containing many students, each with a given_name, surname, and hometown

  # the Program tabe would have many programs, each with
  # a start_date, end_date and market.

  # a Program has many students, so a foregin id key from a Progrma would be placed in a new Program_id column in the Students table.
```

1.  For the above example, what needs to be added to the Model files?

```rb
class Student < ActiveRecord::Base
belongs_to :programs
end
```

```rb
class Program < ActiveRecord::Base
has_many :students
end
```

1.  What is the purpose of our `schema.rb` file? How does it differ from a migration?

```sh
  # the schema.rb is a recorn of all changes made over the course of multiple migrations. It is a total collection of changed in the databse over time
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
  # rails generate migration RemoveAuthorFromBooks author
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
  # The key will go on the Books table because a author has many books. the key is used to reference the author of the specified book.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
  # rails g migration AddAuthorIdToBooks author_id:references

```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
# class Book < ActiveRecord::Base
#   validates_uniqueness_of :books
# end
```
