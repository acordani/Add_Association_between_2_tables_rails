We have 1 table

- Job (title, description, company


We want to have an association between these tables

```sh 
 rails g model Job title:string description:text company:string
```

We want to create a new table  Category (name:string)

```sh 
 rails g model Category name:string
```

We want to add a column called "name" of type string to the "jobs" table 

```sh 
 rails g migration AddNameToJobs name:string
```

And we want to add a column called "category_id" of type string to the "jobs" table 

```sh 
 rails g migration AddCategoryIdToJobs category_id:integer
```

Add associations between tables
- Models > category.rb
```
class Category < ActiveRecord::Base
  has_many :jobs
end
```

- Models > job.rb
```
class Job < ActiveRecord::Base
  belongs_to :category
end
```


And in _form of index job 
```
<div class="form-group">
  <%= f.collection_select :category_id, Category.all, :id, :name, {promt: "Choose a category"} %>
</div>
```
