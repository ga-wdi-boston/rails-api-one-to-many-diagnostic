# Rails API One-to-Many Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  What is one purpose for having relationships in our API?

```sh
  Since many data sets in databases have some type of relationship to one another we need to be able to have those different tables talk to each other in order to display certain
  data that an app might need all together.
```

1.  Provide a database table structure and explain the Entity Relationship
that describes a one-to-many relationship for `Students` and `Programs`.
A `Student` has a `given_name`, `surname`, `hometown` and `nickname` and a
`Program` has `state_date`, `end_date`, and `market`.

```sh
Table 1: Students
- given_name
- surname
- hometown
- nickname
    \|/
     |
     |
Table 2: Program
- start_date
- end_date
- market

The foreign key would be added to students in this case since a program has many students and students belong to a program.

```

1.  For the above example, what needs to be added to the Model files?
```
The data set needs to be defined for each of the models. Students would be:

bundle exec rails g model Student given_name:string surname:string hometown:string nickname:string

Program would be:
bundle exec rails g model Program start_date:date end_date:date market:string

```rb
class Student < ActiveRecord::Base
end
```

```rb
class Program < ActiveRecord::Base
end
```

1.  What is the purpose of our `schema.rb` file? How does it differ from a migration?

```sh
Our schema.rb is a summary of our migrations. This file is for reference purposes only. If we reset the database, it will load from the schema.
```

1.  You have a `Books` table that has the attributes, `title`, `author` and
`release_date`. What would the migration command be to _remove_ the `author`
column?

```sh

in terminal: bundle exec rails g migration RemoveAuthorFromBooks author

in migration file:

class RemoveAuthorFromBooks < ActiveRecord
  def change
    remove_column :author
  end
end
```

1.  You now have an `Authors` table with `given_name`, `surname`, and `born_in`.
Given that you now have a `Books` and `Authors` table, which table will get the
foreign key to allow for a join? Why?

```sh
The foreign key would be added to books because more times than not a book will only have
one author, but an author could have many books. It is convention to put the key on the
table that is the plurality, in this case it is books.
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
