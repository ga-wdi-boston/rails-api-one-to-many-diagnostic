# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
Having relationships in our API allows us to produce a single report
incorporating related data from multiple tables.

It also assists with good maintenance of data. Connecting tables via foreign
keys allows us to use foreign key constraints, which prevent us from deleting
data from one table that still has a relationship to a row in another table.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `start_date`, `end_date`, and `market`.

```sh
Database has two tables: 'students' and 'programs'

Table 'students' has 5 columns in addition to primary key:
`given_name`, `surname`, `hometown`, `nickname` and foreign key 'program_id'

Table 'programs' has 3 columns in addition to primary key:
`start_date`, `end_date`, and `market`

A Program has many Students. A Student belongs to a Program. We could
potentially improve the semantics of our database by specifying this
relationship more clearly, renaming the foreign key 'program_id' to something
like 'enrolled_in'.
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
The schema is a canonical representation of the current state of a database. It
is not an executable file; unlike a migration, the test suite will not load our
'schema.rb' file. Rather, the 'schema.rb' serves as a one-stop summary of all
our migrations, showing what tables we have, what columns they have, and what
relationships exist between them.
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
ALTER TABLE books
DROP COLUMN author;
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
The table 'Books' will get a foreign key, because while an author may have many
books, each book (for purposes of this example) has only one author. Therefore,
it is possible to limit each row in 'Books' to a single foreign key for
author_id.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
ALTER TABLE books
ADD COLUMN author_id INTEGER REFERENCES authors (id);
CREATE INDEX ON books (author_id);
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
Prevent a user from adding a duplicate Book record to the data store by adding
the following 'validates' statement to the Book model:

class Book < ActiveRecord::Base
  validates :title, uniqueness: true
end
```
