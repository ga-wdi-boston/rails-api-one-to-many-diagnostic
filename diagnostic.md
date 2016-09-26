# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
It allows us to have a way to relate multiple different sets of data in a variety of ways.  It gives us bidirectionality when looking up data (we can find the other match in a pair either by the plurality or by the singularity).
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
Student
- given_name
- surname
- hometown
- nickname

Program
- Serial_Primary_ID
- start_date
- end_date
- market
- Students

A program has many students.  A student belongs to a single program.
```

1.  For the above example, what needs to be added to the Model files?

```rb
class Student < ActiveRecord::Base
  serial_Primary_ID  # SQL does this for us though
  program_ID
end
```

```rb
class Program < ActiveRecord::Base
  Students
end
```

1.  What is the purpose of our `schema.rb` file? How does it differ from a migration?

```sh
  The schema keeps track of changes to your database (which happen when a database is migrated).  A migration is the change itself, either to the format or content (changing/adding/removing columns, rows, entries, or altering the layout)
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
  remove_column :Books :author
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
  Books will have the foreign key, because a book can only have one author, but an author can have many books, barring exceptions of multiple authorship.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
  add_foreign_key :Authors, :Books
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
INSERT INTO books
VALUES blargh
WHERE NOT EXISTS blargh
```
