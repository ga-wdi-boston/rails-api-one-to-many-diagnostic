# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
Having relationships allows us to link multiple tables, keeping the data consisten throughout.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
Programs have many students

Student Columns : `given_name`, `surname`, `hometown`, `nickname`, `program id`
Program Columns : `state_date`, `end_date`, and `market`
```

1.  For the above example, what needs to be added to the Model files?

```rb
class Student < ActiveRecord::Base
  belongs_to :Program
end
```

```rb
class Program < ActiveRecord::Base
  has_many :students
end
```

1.  What is the purpose of our `schema.rb` file? How does it differ from a migration?

```sh
The Schema file is the current state of your database, it includes all migrations that have occurred.
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
  # < Your Response Here >
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
  # < Your Response Here >
```
