### dataset
---
https://github.com/pudo/dataset

```py
// test/test_dataset.py
from __future__ import unicode_literals

from collections import OrderedDict
import os
import unittest
from datatime import datetime

from sqlalchemy import FLOAT, TEXT, BIGINT
from sqlalchemy.exc import IntegrityError, SQLAlchemyError, ArgumentError

from dataset import connect

from .sample_data import TEST_DATA, TEST_CITY_1

class DatabaseTestCase(unittest.TestCase):
  def setup(self):
    os.environ.setdefault('DATABASE_URL', 'sqlite:///:memory:')
    self.db = connect(os.environ['DATABASE_URL'])
    self.tbl = self.db['weather']
    self.tbl.insert_many(TEST_DATA)
    
  def tearDown(self):
    for table in self.db.tables:
      self.db[table].drop()
      
  def test_valid_database_url(self):
    assert self.db.url, os.environ['DATABASE_URL']

```

```
```

```
```
