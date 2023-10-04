**Django MVT Model and Database**



**Models:**

A model in Django sketches out how data should be structured, detailing its fields and actions. We can consider it as a design sketch for a unique database item. In Django, each model is directly linked to an individual database table.



If we want to create an app to manage a library. One of the things we want to keep track of is books. 



from django.db import models

class Book(models.Model):

    title = models.CharField(max_length=200)

    author = models.CharField(max_length=100)

    published_date = models.DateField()

    isbn_number = models.CharField(max_length=13)

    page_count = models.IntegerField()

    cover_image = models.ImageField(upload_to='books/covers/')

    language = models.CharField(max_length=20)



    def __str__(self):

        return self.title



The Book class is a Django model, which subclasses models.Model.



Every feature of the class is like a column in a database table, and it has a certain kind of data. After we set up this model, Django automatically makes a matching table in the database for us. When we add, view, change, or remove items using this model, Django does the database automatically for us in the background. This means we can work with our database using basic Python, without needing to write complex SQL and use queries.



Resources (Models): 

[Models | Django documentation | Django](https://docs.djangoproject.com/en/3.2/topics/db/models/)



**Routes:**



Routes are also referred to as “URL Patterns” in Django. They define which function or view should be executed when a particular URL is accessed. So it essentially maps different URLs of a web application to different functions and views. 



In our Django project, our routing can be configured in the `urls.py` file. We need to use the `path()` function to map a route to a function or a view. 

![](https://lh3.googleusercontent.com/9JxWe3JL2AQz8v0VSxz29Xd7oAOpfPg0Rebc5gWAvVoTAEJ22t3ZZPjap_ajtPy_j3rLBQkVCgcpwS9xOQMo7rE5h7xKAR4IN1h0P-exfao7Bf0Jvg-_a2NC0zaxmKTXnRO1O35mJaIFtNihbAdclvY)

We can define all of the patterns here. The first element of the array maps an empty path ‘’ to the views.index() function. This is essentially saying that when a user accesses the URL of the site containing an empty path, it will call the views.index() function, which displays the content. This is what the views.index() function looks like:

![](https://lh5.googleusercontent.com/_uQFupVqwSe7oQO799OwDZo_SzkhqL-hSznVAFXpcr95WNwVjIT0jkAkAhF2J2Cb_MKIQeLkzee47Rv9ssC6z-TbzIW_wJW_6L7sBRYi45ML4mkzqgqGtHtMAWd2ftDY9t6W0UMlnfTr1sKXsgRcR5Q)

This will render the index.html file in our project, in the portfolio_app directory.



Resource: [Django Routing Examples &#8211; vegibit](https://vegibit.com/django-routing-examples/)



**Migrating/updating database:**

What is it -

- “The process of migrating data from one or more source databases to one or more target databases by using a database migration service.”

- Source database – Database that contains data to be migrated to another database.

- Target database – Database that receives data migrated from a source database.

- After migration, data from source database resides in the target database (although can be restructured in the target database.

![](https://lh4.googleusercontent.com/7koH6nrcU-SV2RRHBCFHCGYliAIGHn9S0q38VTILd-35ChvYA5jX1VXt1GtCNaFc-cHRShOZAvwLfrhDplyngt2ya2WPFL-Zjubxn7jwEOLwsYlhNjsXRgYj5MoZ7TRIvh1vGptZz6qsJIFaGi2mBZs)

- Homogenous database migration – Migration from source databases to target databases where the source and target database are of the same database management system.

- Heterogeneous database migration – Migration from source databases to target databases where the source and target databases are of different database management systems from different providers.

- Database migration system - A software system or service that connects to source databases and target databases and performs data migrations from source to target databases.

When to do it -

- When upgrading or updating the database to a newer version (new features, security, performance, etc.)

- A lot more reasons explained here: [Database Migration Best Practices](https://chat.openai.com/share/d21f99ee-6de5-4bfe-a617-22fdae73f7b3)

How to do it -

- ![](https://lh5.googleusercontent.com/2quN4xoko4dqMCfIWOpfJffuNHPij3JeHoVsJHAnRkuUIrGMA1NW5HndNtyoDtCffotV5BnBSFCHV1dMySduhslVOkflq6Ms1wzllu2Lv-9yGwUh7mwRxKRmZhiYCpXIoIMcSdGZmlgOXwXuPpSK-UA)

- [Migrations | Django documentation | Django](https://docs.djangoproject.com/en/4.2/topics/migrations/)

- [How to create database migrations | Django documentation | Django](https://docs.djangoproject.com/en/4.2/howto/writing-migrations/)

- The migration files for each app live in a “migrations” directory inside of that app, and are designed to be committed to, and distributed as part of, its codebase.

- Ex.) $ python manage.py makemigrations → $ python manage.py migrate

- Resetting database - [Reset Database in Django | Delft Stack](https://www.delftstack.com/howto/django/django-reset-database/)



**Relationships:**



Django offers a powerful and flexible Object-Relational Mapping system that allows developers to define various types of relationships using model fields.



ForeignKey (One-to-Many Relationship):

A ForeignKey establishes a one-to-many relationship. This means that one record in a model can be related to multiple records in another model. If we consider a Blog model and a Comment model. One Blog post can have many Comments, but each Comment can only have one Blog.



class Blog(models.Model):
title = models.CharField(max_length=200)

class Comment(models.Model):
blog = models.ForeignKey(Blog, on_delete=models.CASCADE)
text = models.TextField()



OneToOneField (One-to-One Relationship):

A OneToOneField establishes a one-to-one relationship between two models. Each record in one model relates to one and only one record in the other model.
If we have a User model and a Profile model where each user has one profile, and each profile belongs to one user, we would use OneToOneField.



class User(models.Model):
username = models.CharField(max_length=100)

class Profile(models.Model):
user = models.OneToOneField(User, on_delete=models.CASCADE)
bio = models.TextField()



ManyToManyField (Many-to-Many Relationship):

A ManyToManyField allows multiple records in one model to relate to multiple records in another model. If we consider a Book model and an Author model. A book can have multiple authors, and an author can write multiple books.



class Author(models.Model):
name = models.CharField(max_length=100)

class Book(models.Model):
title = models.CharField(max_length=200)
authors = models.ManyToManyField(Author)



Relationship Attributes:

on_delete: This attribute determines what should happen when a related object is deleted. Options include models.CASCADE, models.PROTECT, models.SET_NULL, and more. related_name: This provides a reverse relation from the related model back to the model defining the relationship. It is useful for querying from the other side of the relationship.



Here is a visual representation that shows all the types of relationships: 

![](C:\Users\mabra\AppData\Roaming\marktext\images\2023-10-04-17-04-09-image.png)

**Active Records:**

https://sd.blackball.lv/library/patterns_of_enterprise_application_architecture_(2002).pdf 



Martin Fowler’s Active Record pattern is used to take all data from an object and surround it in the domain of the object so that it is easier to read and write to the database. This data contains everything that pertains to that object, such as its behavior. All data for the object is put into a table where objects are split by rows and all behaviors and characteristics are split through columns.  

In code like Java or C#, this would be like making a class for an object with specific variables that are unique to that class of objects. Interacting with the database would be like using getters and setters for those variables.



**Python queries:**



Especially when using frameworks like Django, we want to retrieve, filter, or manipulate data stored in databases without needing to write raw SQL. Instead, we can use Pythonic expressions to represent these operations.



Fetching All Records:

Instead of SELECT * FROM table; in SQL, in Django, we might do:

all_records = ModelName.objects.all()


Filtering Records:

Instead of SELECT * FROM table WHERE condition; in SQL, in Django, we might do:

filtered_records = ModelName.objects.filter(field_name=value)


Fetching a Single Record:

In Django, if we want a single matching record:

single_record = ModelName.objects.get(field_name=value)


Ordering Records:

Instead of ORDER BY in SQL:

ordered_records = ModelName.objects.all().order_by('field_name')


Aggregations:

Instead of SQL's UPDATE:

ModelName.objects.filter(field_name=value).update(another_field=new_value)


Deleting Records:

Instead of SQL's DELETE:

ModelName.objects.filter(field_name=value).delete()


