# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  it allows you to see when two things may be connected. like ingredients in a recipe.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
  table student
    given_name
    surname
    hometown
    nickname
    
  table programs
    start_date 
    end_date
    market

the programs table would have many students because more than one student takes a program. so each student would have a program_id column. 

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
 the schema file's purpose is to set up the structure of our tables.
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
remove_columns(Books, author)
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
the foreign key goes to the book because that is where the id of the author will be. 
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
rails generate migration AddAuthorToBook author_id:string
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
  in the model
    validates :name, :presence => true, :uniqueness => true
```
