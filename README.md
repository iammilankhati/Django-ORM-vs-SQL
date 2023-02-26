## Django ORM vs SQL

_The Django web framework includes a default OBJECT RELATIONAL MAPPING(ORM)
layer that can be used to interact with application data from the various
relational database such as SQLite, postgreSQL, MYSQL, here we have used MYQL
for DJANGO ORM_

:+1:

## Datatype to django model type

_type/django-model-type/mysql-type/description_

### Binary field

- **Binary - models.BinaryField()** - longblog NOT NULL _Creates a blob field to
  store binary data (e.g. images, audios and other multimedia objects)_

### Boolean field

- **Boolean - models.BooleanField()** - bool NOT NULL _Creates a boolean field
  to store True/False values or 0/1_

- **Boolean** - models.NullBooleanField() - bool NULL _Works just like
  BooleanField but allows NULL values_

### Date/Time field

- **Date/Time - models.DateField()** - date NOT NULL _Creates a date field to
  store date_
- **Date/Time - models.TimeField()** - time NOT NULL _Creates a time field to
  store time_
- **Date/Time - models.DateTimeField()** - datetime NOT NULL _Creates a datetime
  field to store dates with time_
- **Date/Time** - models.DurationField() - bigint NOT NULL _Creates a field to
  store periods of time_

### Number Field

- **Number - models.AutoField()** - integer AUTO*INCREMENT NOT NULL \_Creates a
  integer that autoincrements, primarily used for custom primary keys*
- **Number** - models.DecimalField(decimal*places=X, max_digits=Y) -
  decimal(X,Y) NOT NULL \_Enforces a number have maximum of Y digits and Y
  decimal points. Creates decimal fields to store decimal numbers. Note both X
  and Y arguments are required, where X arguments represents the maximum number
  of digits to store and Y argument represents the decimal places to store*
- **Number - models.FloatField()** - real NOT NULL _Creates a column to store
  floating point numbers_
- **Number - models.IntegerField()** - integer NOT NULL _Creates a column to
  store integer numbers_
- **Number** - models.BigIntegerField() - bigint NOT NULL _Creates a big integer
  to fit number between -9223372036854775808 to 9223372036854775807_
- **Number** -options.SmallIntegerField() - smallint NOT NULL _Creates a column
  to store -32768 to 32768_
- **Number** - models.PositiveIntegerField() - integer unsigned NOT NULL
  _Creates a column to store integer from 0 to 2147483647_
- **Number** - models.PositiveSmallIntegerField() - smallint unsigned NOT NULL
  _Creates a column to store number from 0 to 32768_

### Text Field

- **Text** - models.CommaSeperatedIntegerField(max*length=50) -varchar(N) NOT
  NULL \_Store CSV of Integers (e.g. 3,25,12,96)*
- **Text - models.CharField(max_length=N)** - varchar(N) NOT NULL _Creates text
  column, where the max_length argument is required to speficy the maximum
  length in characters_
- **Text - models.TextField()** - longtext NOT NULL _Creates a textfield_
- **Text - models.EmailField()** - varchar(254) NOT NULL _Creates email field
  with internal email validator_
- **Text - models.FileField()** - varchar(100) NOT NULL _Creates and provides
  utilities to handle files(e.g. opening/closing file, upload location etc) also
  checks if it is a file_
- **Text - models.FilePathField()** - varchar(100) NOT NULL _limits the choices
  of filenames in certain directory_
- **Text - models.ImageField()** - varchar(100) NOT NULL _pip install pillow to
  to use this, set height, width_
- **Text** - models.GenericIPAddressField() - char(39) NOT NULL _accepts only
  valid ipv4 or ipv6_
- **Text - models.SlugField()** - varchar(50) NOT NULL _accepts a slug -
  hypens,letters, underscores,numbers and cleans the URL_
- **Text - models.URlField()** - varchar(200) NOT NULL _accepts the valid URL_
- **Text - models.UUIDField()** - char(32) NOT NULL _Ensures the provided text
  is Universally unique identifiers_

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

### Fetching

1. Fetch All Row

**SQL**

```
SELECT * FROM Person
```

**Django**

```
persons = Person.objects.all()

for person in persons:
    print(person.name)
    print(person.age)
    print(person.gender)
```

2. Fetch specific column

**SQL**

```
SELECT name, age FROM Person;
```

**Django**

```
Person.objects.only('name', 'age')
```

3. Fetch distinct rows

**SQL**

```
SELECT DISTINCT name, age FROM Person
```

**Django**

```
Person.objects.values('name', 'age').distinct()
```

4. Limiting the number of rows fetch

**SQL**

```
SELECT * FROM Person LIMIT 10;
```

**Django**

```
Person.objects.all()[:10]
```

5. Limiting and Offsetting

**SQL**

```
SELECT * FROM Person OFFSET 5 LIMIT 10;
```

**Django**

```
Person.objects.all()[5:15]
```

### Filtering

1. Filtering by single column **SQL**

```
SELECT * FROM Person where id=3;
```

**Django**

```
Person.objects.filter(id=1)
```

1. Filtering by comparision operator **SQL**

```
SELECT * FROM Person where id > 4
SELECT * FROM Person where id >= 4
SELECT * FROM Person where id < 4
SELECT * FROM Person where id <= 4
SELECT * FROM Person where id != 4
```

**Django**

```

Person.objects.filter(id__gt = 4)
Person.objects.filter(id__gte = 4)
Person.objects.filter(id__lt = 4)
Person.objects.filter(id__lte = 4)
Person.objects.exclude(id =4)

```

1. Filtering by between

**SQL**

```
SELECT * FROM Person where id between 1 and 3
```

**Django**

```
Person.objects.filter(id__range =(1,3))
```

1. Filtering by like

**SQL**

```
SELECT * FROM Person where name like '%A%'
SELECT * FROM Person where name like binary '%A%'
SELECT * FROM Person where name like '%A'
SELECT * FROM Person where name like binary '%A'
SELECT * FROM Person where name like 'A%'
SELECT * FROM Person where name like binary 'A%'

```

**Django**

```
Person.objects.filter(name__icontains ='A')
Person.objects.filter(name__contains ='A')
Person.objects.filter(name__istartswith ='A')
Person.objects.filter(name__startswith ='A')
Person.objects.filter(name__iendswith ='A')
Person.objects.filter(name__endswith ='A')
```

1. Filtering by In

```
SELECT * FROM Person where id in (1,2)
```

**Django**

```
Person.objects.filter(id__in=[1,2])
```
