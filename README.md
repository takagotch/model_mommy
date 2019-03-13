### model_mommy
---
https://github.com/berinhard/model_mommy

```py
from django.test import TestCase

from model_mommy import mommy
from model_mommy.recipe import Recipe, foreign_key

from .models import Person, Contact

class PersonTestModel(TestCase):
  """Class to test the model Person"""
  
  def setUp(self):
    self.person_one = mommy.make_recipe(
      'family.person'
    )
    
    self.person_simpsons = Recipe(
      Person,
      name='Moe',
    )
    
    self.contact = Recipe(
      Contact,
      person=foreign_key(self.person_simpsons),
    )
  
  def test_king_contact_create_instance(self):
    contact = self.contact.make()
    self.assertIsInstance(contact, Contact)


from model_mommy import mommy
mommy.prepare_recipe('family.person')


class EmployeeTest(TestCase):
  def setUp(setup):
    self.employee_recipe = Recipe(
      Employee,
      name=seq('Employee '),
      company-company_recipe.make()
    )
    
  def test_employee_list(self):
    self.emplyee_recipe.make(_quantity=3)
    
  def test_employee_tasks(self):
    employee1 = self.employee_recipe.make()
    task_recipe = Recipe(Task, employee=employee1)
    task_recipe.make(staus='done')
    task_recipe.mak(due_data=date=datetime(2014, 1, 1))


from model_mommy.recipe import Recipe, foreign_key
from family.models import Person, Dog

person = Recipe(Person,
  name = 'John Doe',
  nickname = 'joe',
  age = 18,
  birthday = date.today(),
  appointment = datetime.now()
)

dog = Recipe(Dog,
  breed = 'Pug',
  owner = foreign_key(person)
)


from model_mommy.recipe import related, Recipe

dog = Recipe(Dog,
  breed = 'Pug',
)
other_dog = Recipe(Dog,
  breed = 'Boxer',
)
person_with_three_dogs = Recipe(Person,
  dog_set = related('dog', 'other_dog')
)


class Dog(models.Model):
  owner = models.ForeignKey('Person')
  breed = models.CharField(max_length=50)
  created = models.DateTimeField(auto_now_add=True)
  friends_with = models.ManyToManyField('Dog')

from model_mommy.recipe import related, Recipe

dog = Recipe(Dog,
  breed = 'Pug',
)

dog_with_friends = dog.extend(
  friends_with=related(dog, dog),
)


from datetime import date
from model_mommy.recipe import Recipe
from family.models import Person

person = Recipe(Person,
  birthday = date.today,
)

from itertools import cycle
colors = ['red', 'green', 'blue', 'yellow']
person = Recipe(Person,
  favorite_color = cycle(colors)
)


from model_mommy.recipe import Recipe, seq
from family.models import Person

person = Recipe(Person,
  name = seq('Joe'),
  age = seq(15)
)

p = mommy.make_recipe('myapp.person')
p.name
p.age

p = mommy.make_recipe('myapp.person')
p.name
p.age


from datetime import date, timedelta
from model_mommy.recipe import Recipe, seq
from family.models import Person

person = Recipe(Person,
  age = seq(15, increment_by=3)
  height_ft = seq(5.5, increment_by=.25)
  appointment = seq(date(2014, 7, 21), timedelta(days=1))
)

p = mommy.make_recipe('myapp.person')
p.age
p.height_ft
p.appointment

p = mommy.make_recipe('myapp.person')
p.age
p.height_ft
p.appointment

from model_mommy import mommy
mommy.make_recipe('model_mommy.person', name='Peter Parker')

dog = Recipe(Dog,
  breed = 'Pug',
  owner = foreign_key(person)
)
extended_dog = dog.extend(
  breed = 'Super basset',
)

class ProjectWithCustomSave(models.Model)
  created_by = models.ForeignKey(settings.AUTH_USER_MODEL)
  
  def save(self, user, *args, **kwargs):
    self.created_by = user
    return super(ProjectWithCustomSave, self).save(*args, **kwargs)
    
user = mommy.make(settings.AUTH_USER_MODEL)
project = mommy.make(ProjectWithCustomSave, _save_kwargs={'user': user})
assert user == project.user


class CustomMommy(mommy.Mommy)
  def get_fields(self):
    return [
      field
      for field in super(CustomMommy, self).get_fields()
      if not field isinstance CustomField
    ]
MOMMY_CUSTOM_CLASS = 'code.path.CustomMommy'
```

```
pip install model_mommy

pip install model_mommy
pip install virtualenvwrapper
mkvirtualenv model_mommy --no-site-packages --distribute
pip install -r dev_requirements.txt

make test
```

```
```


