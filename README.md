# LordOfTheRings SDK

## Installation

```bash
pip install AaronBlaser-SDK==1.0.1
```

## Usage

1. Import the LordOfTheRings class

```python
from lordoftherings import LordOfTheRings
```

2. Initialize the class with your API Token

```python
api = LordOfTheRings('YOUR API TOKEN')
```

3. Make calls to the API

- /movie
```python
all_movies = api.movies().get_all().fetch()
```
- /movie/{id}
```python
movie = api.movies("5cd95395de30eff6ebccde56").get()
```
- /movie/{id}/quote
```python
movie_quotes = api.movies("5cd95395de30eff6ebccde5b").quotes.get_all().fetch()
```
- /quote
```python
quotes = api.quotes().get_all().fetch()
```
- /quote/{id}
```python
single_quote = api.quotes("5cd96e05de30eff6ebccebc9").get()
```

4. Make calls using sorting, filtering, and pagination

- Filtering
```python
match = api.movies().get_all().filter_by(name='The Lord of the Rings Series').fetch() 
negate_match = api.movies().get_all().filter_by(name=('not', 'The Lord of the Rings Series')).fetch() 
include = api.movies().get_all().filter_by(name=['The Lord of the Rings Series', 'The Desolation of Smaug']).fetch()
exclude = api.movies().get_all().filter_by(name=[('not', 'The Lord of the Rings Series'), ('not', 'The Desolation of Smaug')]).fetch()
less_than = api.movies().get_all().filter_by(budgetInMillions=('<', 100)).fetch() 
greater_than = api.movies().get_all().filter_by(runtimeInMinutes=('>', 160)).fetch()
```

- Sorting
```python
sorted_movies = api.movies().get_all().sort_by("name:asc").fetch()
```

- Pagination
```python
paged_movies_1 = api.movies().get_all().limit(2).fetch()
paged_movies_2 = api.movies().get_all().limit(3).page(2).fetch()
paged_movies_3 = api.movies().get_all().limit(1).page(1).offset(1).fetch()
```

- Combine all Three
```python
filter_sorted_paged = api.movies().get_all().limit(5).filter_by(name=('not', 'The Lord of the Rings Series')).sort_by('name:asc').fetch()
```

## Testing

1. Unit Tests

There is a file called test_lordoftherings.py in the tests folder that has some unit tests in it. Run this file to run the tests

- Replace with your token
    ```python
    self.auth_token = 'YOUR API TOKEN'
    ```

2. Example Usage File

There is a file called test_usage.py in the tests that has many examples of how you can use this SDK. Add your auth token and uncomment
the examples you want to run, then run the file.

- Replace with your token
    ```python
    api = LordOfTheRings('YOUR API TOKEN')
    ```



