# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  One purpose for having relationships is so that we have the ability to link
  data that exist on separate tables.

  source: class notes
  comfort and clarity: 5
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
rails g model Student given_name:string surname:string hometown:string nickname:string

rails g model Program start_date:date end_date:date market:date

A program has many students.
A student belongs to a program.

source: class notes
comfort and clarity: 3

```

1.  For the above example, what needs to be added to the Model files?

```rb
class Student < ActiveRecord::Base
belongs_to :Program
end

source: class notes and lab
comfort and clarity: 5
```

```rb
class Program < ActiveRecord::Base
has_many :Students
end
```

1.  What is the purpose of our `schema.rb` file? How does it differ from a migration?

```sh
The schema.rb file contains the most recent structure of our database and tables. It is
what is constructed after a migration is run. A migration is what helps build the schema.

comfort and clarity: 5
source: class notes
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh
bin/rails g migration RemoveAuthorFromBooks

comfort and clarity: 5
source: class notes

```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
The books table will get the author_id foreign key because an author has many books.
```

1.  Given your answer from above, what would the command be to _add_ the correct **reference** column, to the correct table?

```sh
class AddAuthorRefToBooks < ActiveRecord::Migration
  def change
    add_reference :books, :author, index: true, foreign_key: true
  end
end

comfort and clarity: 4
source: class notes
```

BONUS

1.  How would you prevent a user from adding a `Book`, that has already been added
to the data store?

```sh
class AddUniquenessConstraintToBooks < ActiveRecord::Migration
  add_index
    :title => "udx_entry_on_user_and_product", :unique => true
end

source: http://stackoverflow.com/questions/16919647/rails-how-to-restrict-user-from-entering-more-than-one-record-per-association
```
