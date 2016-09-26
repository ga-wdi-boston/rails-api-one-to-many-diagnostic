# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indicated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  It keeps data organized and consistent. Example: a user can look up several
  books by a single author because the books and the author have a "relationship"
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
#I'm not sure what the first part of the question is asking...
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
  # They represent the current state of the database and cannot be edited. Migrations are used to update the database, which is ultimately shown in schema.
  # http://guides.rubyonrails.org/v3.2.8/migrations.html#what-are-schema-files-for
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
  # remove_column :Books, :author
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
  # I think Books, but I'm not sure...
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
  # rails g migration AddAuthorToBooks author:references
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
  # < Your Response Here >
```
