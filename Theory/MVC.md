# Models
- Contains the essential fields and behaviours of the data you are storing in the DB
- Relationships
	- **Many to one relationships**: This is declared with ForeignKey. It also supports recursive relationships (an object with a many to one relationship to itself) and relationships to models not yet defined
	 ```
	 from django.db import models
	
	 class Manufacturer(models.Model):
		# ...
		pass
	
	 class Car(models.Model):
		manufacturer = models.ForeignKey(Manufacturer, on_delete=models.CASCADE)
		# ...
	 ```
	 
	 ```
	# shows a recursive relationship, the Car.Manufacturer will point to Manufacturer class here.


	from django.db import models

	class AbstractCar(models.Model):
		manufacturer = models.ForeignKey('Manufacturer', on_delete=models.CASCADE)

	class Manufacturer(models.Model):
		pass

	class Car(AbstractCar):
		pass
	 
	 ```
	 - 
- [Model field reference](https://docs.djangoproject.com/en/4.0/ref/models/fields/#lazy-relationships) contains the API references of fields including field options and field types
	- **Field types**
		-  null
		- blank
		- choices: as a list of tuples
		- Enumeration: An improvement on the choices abstracted into a 
		```
		# Here the enum is abstracted into a class of integer choices
		class Card(models.Model):
	
	    class Suit(models.IntegerChoices):
	        DIAMOND = 1
	        SPADE = 2
	        HEART = 3
	        CLUB = 4
	
	    suit = models.IntegerField(choices=Suit.choices)
		```

	- **Field options**
		- db_column: the name of db column to use for the field
		- db_index: a boolean value to determine creation of db_index
		- db_tablespace:
		- default: Takes the default value, lambdas cant be used in this case
		- editable: the field is not displayed in the admin or other model forms and skipped during validation
		- error_messages: Lets user to define custom error messages
		- primary_key: If true, the field take 'id' place as an identifier
		- unique: field must be unique throughtout the table if true
		- unique_for_date
		- unique_for_month
		- unique_for_year
		- verbose_name
		- [validators](https://docs.djangoproject.com/en/4.0/ref/validators/): List of validators to run for the field. 
			- 