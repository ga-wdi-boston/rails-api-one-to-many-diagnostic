# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  If two tables are using the same/very similar information, it makes sense to
  keep them separate and join them later so that when that information ever needs
  to change, it will only have to be updated in one place.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
  Not sure exactly what format this is looking for (and assuming each student
  belongs to a program), but:

  Student
  _______
  id (primary serial)
  given_name:string
  surname:string
  hometown:string
  nickname:string
  program_id:references

  Program
  _______
  id (primary serial)
  state_date:date
  end_date:date
  market:string

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
  The schema is sort of like a cheat sheet set of commands and objects that
  describes the current state of the database. If those commands were run in
  order, the database could be created from scratch again. This is different
  from a migration because migrations were the individual steps taken to get
  the database to its current state. It is possible that these steps are the
  same as those shown in the schema, but it is more likely that the migrations
  have extra steps that add some values, remove others, and make extra
  modifications that are no longer necessary to achieve the desired state of the
  database. It is also possible to get the current state of the database by
  running each migration in order, but this would take longer than running the
  schema file.
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
  rails g migration RemoveAuthorFromBooks author
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
  Books will get the foreign key to allow for a join. In this example, each book
  belongs to an author, so each author has many books. When this is the situation,
  each book will only have one author, so it makes sense to add an author id to
  the books table because there can only be one author per book, so we will only
  need the one column to store that information. If we had put it in the authors
  table, we would not know how many columns were needed to store books for a
  given author.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
  rails g migration AddAuthorToBooks author:references
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
  uniqueness: true
```
