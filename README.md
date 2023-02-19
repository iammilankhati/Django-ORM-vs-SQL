## Django ORM vs SQL



_The Django web framework includes a default OBJECT RELATIONAL MAPPING(ORM)  layer that can be used to interact with application data from the various relational database such as SQLite, postgreSQL, MYSQL, here we have used MYQL for DJANGO ORM_

:+1:

## Datatype to django model type

_type/django-model-type/mysql-type/description_

### Binary field
 
- **Binary - models.BinaryField()** - longblog NOT NULL *Creates a blob field to store binary data (e.g. images, audios and other multimedia objects)*


### Boolean field

- **Boolean - models.BooleanField()** - bool NOT NULL *Creates a boolean field to store True/False values or 0/1*

- **Boolean** - models.NullBooleanField() - bool NULL *Works just like BooleanField but allows NULL values*


### Date/Time field

- **Date/Time - models.DateField()** - date NOT NULL *Creates a date field to store date*
- **Date/Time - models.TimeField()** - time NOT NULL *Creates a time field to store time*
- **Date/Time - models.DateTimeField()** - datetime NOT NULL *Creates a datetime field to store dates with time*
- **Date/Time** - models.DurationField() - bigint NOT NULL *Creates a field to store periods of time*

### Number Field

- **Number - models.AutoField()** - integer AUTO_INCREMENT NOT NULL *Creates a integer that autoincrements, primarily used for custom primary keys*
- **Number** - models.DecimalField(decimal_places=X, max_digits=Y) - decimal(X,Y) NOT NULL *Enforces a number have maximum of Y digits and Y decimal points. Creates decimal fields to store decimal numbers. Note both X and Y arguments are required, where X arguments represents the maximum number of digits to store and Y argument represents the decimal places to store*
- **Number - models.FloatField()** - real NOT NULL *Creates a column to store floating point numbers*
- **Number - models.IntegerField()** - integer NOT NULL *Creates a column to store integer numbers*
- **Number** - models.BigIntegerField() - bigint NOT NULL *Creates a big integer to fit number between -9223372036854775808 to 9223372036854775807*
- **Number** -options.SmallIntegerField() - smallint NOT NULL *Creates a column to store -32768 to 32768*
- **Number** - models.PositiveIntegerField() - integer unsigned NOT NULL *Creates a column to store integer from 0 to 2147483647*
- **Number** - models.PositiveSmallIntegerField() - smallint unsigned NOT NULL *Creates a column to store number from 0 to 32768*

### Text Field
- **Text** - models.CommaSeperatedIntegerField(max_length=50) -varchar(N) NOT NULL *Store CSV of Integers (e.g. 3,25,12,96)*
- **Text - models.CharField(max_length=N)**  - varchar(N) NOT NULL *Creates text column, where the max_length argument is required to speficy the maximum length in characters*
- **Text - models.TextField()** - longtext NOT NULL *Creates a textfield*
- **Text - models.EmailField()** - varchar(254) NOT NULL *Creates email field with internal email validator* 
- **Text - models.FileField()** - varchar(100) NOT NULL *Creates and provides utilities to handle files(e.g. opening/closing file, upload location etc) also checks if it is a file*  
- **Text - models.FilePathField()** - varchar(100) NOT NULL *limits the choices of filenames in certain directory*
- **Text - models.ImageField()** - varchar(100) NOT NULL *pip install pillow to to use this, set height, width*
- **Text** - models.GenericIPAddressField() - char(39) NOT NULL *accepts only valid ipv4 or ipv6* 
- **Text - models.SlugField()** - varchar(50) NOT NULL *accepts a slug - hypens,letters, underscores,numbers and cleans the URL*
- **Text - models.URlField()** - varchar(200) NOT NULL *accepts the valid URL*
- **Text - models.UUIDField()** - char(32) NOT NULL *Ensures the provided text is Universally unique identifiers*


## Similarities in commands

### Table creation 
**SQL**
``` 
CREATE TABLE Person(
    id int,
    name varchar(255),
    age int NOT NULL,
    gender varchar(10),

)
```
**Django**
``` 
Class Person(models.Model):
    name = models.CharField(max_length=50, blank=True)
    age = model.IntegerField()
    gender = model.CharField(max_length=10, blank=True)
```