# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  To show how different object or data are connected
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
  `Student`(`given_name`, `surname`, `hometown`, `nickname`)
  `Program`(`state_date`, `end_date`, `market`)
  The one to many is unclear because I don\'t know how we\'re presenting
  the overall information. You would have a strict one to one, or a
  one program, many students, or one student many programs.
  I\'ll assume it\'s one program many students. this means the students
  would have a program id.
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
  the purpose of the schema is to show the data structure for our information.
  The migrations are building blocks that add to the schema.
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh

class RemoveAuthorFromBooks < ActiveRecord::Migration
  def change
    remove_column :books, :author
  end
end
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
  I would assume that a Author would have many books because it is more common
  than the books having many authors. Because we\'re only storing one item
  of information with the foriegn key we would place it on the books.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
class AddDoctorReferenceToBooks < ActiveRecord::Migration
  def change
    add_reference :books, :author, index: true, foreign_key: true
  end
end
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
  validates :title, uniqueness: true
```
