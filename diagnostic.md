# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
The purpose of having relationships in our api is so that we can make it easier
to access whatever information we want.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
A Program typically has many students, while a Student typically belongs to a single
program at a time. Here is what the table would look like.
Student{
  given_name: ,
  surname: ,
  hometown: ,
  nickname:
  }
Program{
  state_date: ,
  end_date: ,
  market:
}
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
The schema.rb file is where all of the information is updated. This is where all
of the migrations will change the view of the database every time. In my own words,
I would call it the final draft of a project. When we are working on everything
else they would be called the brainstorming/rough drafts.
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
remove_column :books, :author
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
The Books table would have an Author ID foreign key because an author has many
books, and those books belong to an author.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
author_id INTEGER FOREIGN KEY REFERENCES books(author_id)
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
I would change the serializer so that it only allows books that are new.
```
