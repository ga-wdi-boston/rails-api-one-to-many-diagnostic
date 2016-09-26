# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh

Relationships let us connect data (and establish how that data is connected)
without having to replicate that information across tables.

```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh

Note: interpreting "one-to-many relationship for Students and Programs" to
mean "one student, many programs."

Student
- given_name
- surname
- hometown
- nickname

Program
- start_date
- end_date
- market
- student_id


```

1.  For the above example, what needs to be added to the Model files?

```rb
class Student < ActiveRecord::Base
  has_many :programs
end
```

```rb
class Program < ActiveRecord::Base
  belongs_to :student
end
```

1.  What is the purpose of our `schema.rb` file? How does it differ from a migration?

```sh

The schema.rb file describes the current state of the database based on the
migrations that have been run. It doesn't affect the state of the database,
unlike migrations (which change things when they're run).

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

Books will get the foreign key because an author can have many books, but a
book can only have one author.

```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh

bundle exec rails g migration AddAuthorRefToBooks author:references

```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh

You could add validates :title, uniqueness: true to the Book model.

```
