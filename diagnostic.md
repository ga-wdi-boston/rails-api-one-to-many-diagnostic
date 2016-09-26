# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
Relationships in API allow us to share data between tables. A client request can
pull data from two or more tables.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
In this case the student is the one data point with the attributes of given_name,
surname, hometown, and nickname. The proram is also a data point with many attributes
of start_date, end_date and market. There would be table of student and program with
columns corresponding to the attributes. The students can also be tied to the program
vie a program ID in the student table.
```

1.  For the above example, what needs to be added to the Model files?

```rb
class Student < ActiveRecord::Base
belongs_to :program
end
```

```rb
class Program < ActiveRecord::Base
had_many :students
end
```

1.  What is the purpose of our `schema.rb` file? How does it differ from a migration?

```sh
The schema.rb is your data structure. It has table names and data headers for rows
and columns. Migration files show which data tables are being added to the API.
Schema files should never be modified. Migration files can be deleted if there is
an error.
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
rails g migration RemoveAuthorFromBooks author:references
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
  # < Your Response Here >
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
  # < Your Response Here >
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
  # < Your Response Here >
```
