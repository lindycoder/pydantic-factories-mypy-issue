# pydantic-factories-mypy-issue
Demonstrating an issue with the ModelFactory generic type

# Preparation

```
poetry install
```

No Poetry?
```
virtualenv /tmp/poetry
/tmp/poetry/bin/pip install poetry
/tmp/poetry/bin/poetry install
```

# Reproduce

Without specifying a generic type:
```
poetry run mypy example1.py
example.py:17: error: Missing type parameters for generic type "ModelFactory"
```

Specifying the type:
```
poetry run mypy example2.py
example2.py:17: error: Value of type variable "T" of "ModelFactory" cannot be "Person"
```

Specifying the type's type
```
poetry run mypy example3.py
example3.py:17: error: Invalid type argument value for "ModelFactory"
example3.py:18: error: Incompatible types in assignment (expression has type "Type[Person]", base class "ModelFactory" defined the type as "Type[Type[Person]]")
```
