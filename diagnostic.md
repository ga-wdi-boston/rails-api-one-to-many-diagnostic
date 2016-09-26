# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  The purpose of having relationships in our API helps us establish connections between
  different tables so we can easily deligate where data needs to be accessed and shared.

```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
class Student
  def initialize
  end
end
```

1.  For the above example, what needs to be added to the Model files?

```rb
class Student < ActiveRecord::Base
  validates :given-name, :surmane, hometown, nickname => true
end
```

```rb
class Program < ActiveRecord::Base
validates :state_date, :end_date, :market => true
end
```

1.  What is the purpose of our `schema.rb` file? How does it differ from a migration?

```sh
  The schema starts off as an empty file and migration can be used to modify it.
  The ActiveRecord class works with both migration and schema to add, remove and
  update tables in the database
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
  It removes the author column from Books table.
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
  Books would need a foreign key to join because it does not have previlege to author
  columns.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
  def change
    add_reference :author, foreign_key: true
  end

```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
  # < Your Response Here >
```
