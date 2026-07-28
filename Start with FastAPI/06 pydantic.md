## Pydantic — Complete Notes (Interview + Development)
### Data Validation & Settings Management for Python

---

## 📋 Table of Contents

1. [What Problem Does Pydantic Solve?](#1-what-problem-does-pydantic-solve)
2. [Installation & Setup](#2-installation--setup)
3. [Basic Model Creation](#3-basic-model-creation)
4. [Type Coercion vs Strict Mode](#4-type-coercion-vs-strict-mode)
5. [Field() — Constraints & Metadata](#5-field--constraints--metadata)
6. [Optional Fields & Default Values](#6-optional-fields--default-values)
7. [Nested Models](#7-nested-models)
8. [Validators](#8-validators)
9. [Model Config](#9-model-config)
10. [Serialization (model_dump, model_dump_json)](#10-serialization)
11. [Parsing / Deserialization](#11-parsing--deserialization)
12. [Computed Fields](#12-computed-fields)
13. [Custom Types & Annotated](#13-custom-types--annotated)
14. [Generic Models](#14-generic-models)
15. [Enums in Pydantic](#15-enums-in-pydantic)
16. [Union Types & Discriminated Unions](#16-union-types--discriminated-unions)
17. [Error Handling (ValidationError)](#17-error-handling-validationerror)
18. [Settings Management (pydantic-settings)](#18-settings-management-pydantic-settings)
19. [Pydantic Dataclasses](#19-pydantic-dataclasses)
20. [Pydantic v1 vs v2 (Interview Favorite)](#20-pydantic-v1-vs-v2-interview-favorite)
21. [Pydantic + FastAPI Integration](#21-pydantic--fastapi-integration)
22. [Performance Notes](#22-performance-notes)
23. [Common Interview Questions](#23-common-interview-questions)
24. [Cheat Sheet](#24-cheat-sheet)

---

## 1. What Problem Does Pydantic Solve?

### The Core Problem
Python is **dynamically typed** — nothing stops you from passing wrong data types at runtime.

```python
def create_user(name, age):
    return {"name": name, "age": age}

create_user("Alice", "twenty-five")  # No error! Bug hides until it breaks something later
```

When data comes from **external, untrusted sources** — API requests, JSON files, environment variables, database rows, user forms — you have **no guarantee** it matches the shape/type you expect.

### Problems Without Pydantic
| Problem | Example |
|---------|---------|
| No type enforcement | `age = "25"` accepted where int expected |
| Manual validation boilerplate | Writing `if not isinstance(...)` everywhere |
| Inconsistent error messages | Every dev writes their own validation errors |
| No single source of truth for schema | Data shape scattered across code |
| Hard to serialize/deserialize consistently | Manual `dict()`/`json.dumps()` handling |
| No IDE autocomplete on raw dicts | `data["nmae"]` typos go unnoticed |

### What Pydantic Gives You
1. **Automatic validation** using Python type hints — no boilerplate
2. **Automatic type coercion** ("25" → 25) where sensible
3. **Clear, structured error messages** telling you exactly what failed and where
4. **Serialization** to dict/JSON out of the box
5. **IDE & static-analysis friendly** — autocomplete, type checking (mypy)
6. **Single source of truth** — model defines shape once, used everywhere
7. **Nested & complex validation** — deeply nested JSON structures validated recursively
8. **Settings/config management** — validate environment variables, `.env` files
9. **Speed** — Pydantic v2's core validation logic is written in **Rust** (via `pydantic-core`), making it one of the fastest validation libraries for Python

### Where It's Used in Real Life
- **FastAPI** — request/response validation (the #1 reason people learn Pydantic)
- **LangChain / LLM tooling** — structured output validation
- **Django Ninja, Litestar** — other web frameworks
- **Config/settings management** — env vars, `.env` files, secrets
- **Data pipelines / ETL** — validating incoming records
- **SQLModel** — combines SQLAlchemy + Pydantic

---

## 2. Installation & Setup

```bash
pip install pydantic

# For settings management (env vars, .env files)
pip install pydantic-settings

# Check version
python -c "import pydantic; print(pydantic.VERSION)"
```

> **Interview tip:** Be ready to say "I use Pydantic v2" — it's a common differentiator since v1 → v2 was a near-total rewrite (rewritten core in Rust) with breaking API changes.

---

## 3. Basic Model Creation

### Defining a Model

```python
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    is_active: bool = True   # default value

# Creating an instance
user = User(id=1, name="Alice")
print(user)              # id=1 name='Alice' is_active=True
print(user.id)           # 1 (attribute access)
print(type(user))        # <class '__main__.User'>
```

### What Happens Under the Hood
1. Pydantic reads the **type annotations** of the class
2. When you instantiate it, it **validates every field** against its declared type
3. If valid → coerces to the right type & creates the instance
4. If invalid → raises `pydantic.ValidationError` with detailed info

### Validation on Creation

```python
user = User(id="1", name="Alice")  # "1" (str) → coerced to 1 (int)
print(user.id, type(user.id))      # 1 <class 'int'>

user = User(id="abc", name="Alice")  
# ❌ raises ValidationError: id -> Input should be a valid integer
```

---

## 4. Type Coercion vs Strict Mode

### Lax Mode (Default) — Coerces Compatible Types

```python
class Product(BaseModel):
    price: float

p = Product(price="19.99")   # str -> float ✅ coerced
print(p.price)               # 19.99
print(type(p.price))         # <class 'float'>
```

### Strict Mode — No Coercion Allowed

```python
from pydantic import BaseModel, Field

class Product(BaseModel):
    price: float = Field(strict=True)

Product(price="19.99")  # ❌ ValidationError: Input should be a valid number
Product(price=19.99)    # ✅ Works
```

### Model-Wide Strict Mode

```python
from pydantic import BaseModel, ConfigDict

class Product(BaseModel):
    model_config = ConfigDict(strict=True)
    price: float

# OR at call-time
Product.model_validate({"price": 19.99}, strict=True)
```

> **Interview tip:** Explain that Pydantic's "lax mode" is what makes it so convenient for web APIs — query params/form data arrive as strings but get coerced to int/float/bool automatically. Strict mode is for when you need byte-for-byte type guarantees (e.g., internal service-to-service APIs).

---

## 5. Field() — Constraints & Metadata

`Field()` lets you add validation rules, defaults, aliasing, and documentation to a field.

```python
from pydantic import BaseModel, Field

class User(BaseModel):
    name: str = Field(min_length=2, max_length=50)
    age: int = Field(gt=0, le=120)                    # gt=greater than, le=less/equal
    email: str = Field(pattern=r"^\S+@\S+\.\S+$")
    username: str = Field(default="anonymous")
    score: float = Field(default=0.0, ge=0, le=100)    # ge = greater/equal
```

### Common Field Constraints

| Constraint | Applies To | Meaning |
|-----------|-----------|---------|
| `gt`, `ge` | numbers | greater than / greater-or-equal |
| `lt`, `le` | numbers | less than / less-or-equal |
| `min_length`, `max_length` | str, list, etc. | length bounds |
| `pattern` | str | regex pattern match |
| `multiple_of` | numbers | must be multiple of value |
| `default` | any | default value |
| `default_factory` | any | callable that generates default (for mutable defaults) |
| `alias` | any | alternate name used during input/output |
| `frozen` | any | field can't be changed after creation |
| `description` | any | docs/metadata (shows in JSON schema / OpenAPI) |

### `default_factory` (Important for Mutable Defaults)

```python
from datetime import datetime
from pydantic import BaseModel, Field

class Order(BaseModel):
    items: list[str] = Field(default_factory=list)   # ✅ avoids shared mutable default bug
    created_at: datetime = Field(default_factory=datetime.now)
```

> **Why not `items: list[str] = []`?** Same classic Python gotcha as mutable default arguments — all instances would share the same list object. `default_factory` creates a fresh one per instance.

### Field Aliasing (Common in APIs with camelCase)

```python
from pydantic import BaseModel, Field, ConfigDict

class User(BaseModel):
    model_config = ConfigDict(populate_by_name=True)
    
    user_name: str = Field(alias="userName")

# Input can use the alias
u = User(userName="Alice")     # ✅ works via alias
u = User(user_name="Alice")    # ✅ also works since populate_by_name=True
print(u.model_dump(by_alias=True))  # {'userName': 'Alice'}
```

---

## 6. Optional Fields & Default Values

```python
from typing import Optional
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    nickname: Optional[str] = None    # can be None, defaults to None
    age: int | None = None            # Python 3.10+ syntax, same meaning
    bio: str = ""                     # not Optional, just has a default
```

### ⚠️ Common Confusion (Interview Trap!)
> `Optional[str]` just means the type can be `str` OR `None`. It does **NOT** make the field optional to provide — you still need `= None` (or another default) to make it *not required*.

```python
class Bad(BaseModel):
    nickname: Optional[str]      # ❌ still REQUIRED (no default given)

class Good(BaseModel):
    nickname: Optional[str] = None   # ✅ actually optional
```

---

## 7. Nested Models

Pydantic validates **recursively** — models can contain other models, lists of models, dicts, etc.

```python
from pydantic import BaseModel

class Address(BaseModel):
    city: str
    zip_code: str

class User(BaseModel):
    name: str
    address: Address                # nested model
    tags: list[str] = []
    friends: list["User"] = []      # self-referencing (forward ref)

data = {
    "name": "Alice",
    "address": {"city": "Kolkata", "zip_code": "700001"},
    "tags": ["admin", "verified"]
}

user = User(**data)
print(user.address.city)   # Kolkata (nested model, dot access)
```

### List of Nested Models

```python
class Order(BaseModel):
    items: list[dict]

class Cart(BaseModel):
    orders: list[Order]

cart = Cart(orders=[{"items": [{"name": "Book"}]}])
```

### Validation Errors Show Full Path

```python
User(name="Bob", address={"city": "Delhi"})  
# ❌ ValidationError: address.zip_code -> Field required
```

---

## 8. Validators

Pydantic v2 has **two decorators** for custom validation logic: `@field_validator` (per field) and `@model_validator` (across the whole model).

### `@field_validator` — Single Field Validation

```python
from pydantic import BaseModel, field_validator

class User(BaseModel):
    name: str
    age: int

    @field_validator("name")
    @classmethod
    def name_must_not_be_empty(cls, v: str) -> str:
        if not v.strip():
            raise ValueError("name cannot be empty")
        return v.title()   # can transform the value too

    @field_validator("age")
    @classmethod
    def age_must_be_reasonable(cls, v: int) -> int:
        if v < 0 or v > 150:
            raise ValueError("age must be between 0 and 150")
        return v
```

### `mode="before"` vs `mode="after"`

```python
from pydantic import BaseModel, field_validator

class Product(BaseModel):
    price: float

    @field_validator("price", mode="before")   # runs BEFORE type coercion
    @classmethod
    def strip_currency_symbol(cls, v):
        if isinstance(v, str):
            return v.replace("$", "").strip()
        return v

Product(price="$19.99")  # "before" validator strips "$" first, then coerces to float
```

| Mode | Runs | Use Case |
|------|------|----------|
| `before` | Before Pydantic's own type coercion | Cleaning raw input (strip symbols, normalize casing) |
| `after` (default) | After coercion & built-in validation | Business logic checks on already-typed value |

### `@model_validator` — Cross-Field Validation

```python
from pydantic import BaseModel, model_validator

class DateRange(BaseModel):
    start_date: str
    end_date: str

    @model_validator(mode="after")
    def check_dates(self):
        if self.start_date > self.end_date:
            raise ValueError("start_date must be before end_date")
        return self
```

```python
class SignupForm(BaseModel):
    password: str
    confirm_password: str

    @model_validator(mode="after")
    def passwords_match(self):
        if self.password != self.confirm_password:
            raise ValueError("passwords do not match")
        return self
```

### `mode="before"` for Model Validator (raw input dict)

```python
class Form(BaseModel):
    a: int
    b: int

    @model_validator(mode="before")
    @classmethod
    def check_raw_input(cls, data):
        # 'data' here is the raw dict BEFORE any field validation
        if isinstance(data, dict) and "a" not in data:
            data["a"] = 0
        return data
```

---

## 9. Model Config

Configuration controls model-wide behavior. In v2, use `model_config = ConfigDict(...)`.

```python
from pydantic import BaseModel, ConfigDict

class User(BaseModel):
    model_config = ConfigDict(
        str_strip_whitespace=True,   # auto .strip() all str fields
        str_to_lower=True,           # auto lowercase all str fields
        frozen=True,                 # make instance immutable
        extra="forbid",              # forbid unknown fields (or "allow" / "ignore")
        populate_by_name=True,       # allow both alias and field name as input
        validate_assignment=True,    # re-validate when attributes are reassigned
        from_attributes=True,        # allow creating from ORM objects (was orm_mode in v1)
    )

    name: str
    email: str
```

### Key Config Options Explained

| Option | Purpose |
|--------|---------|
| `extra` | `"ignore"` (default) drop unknown fields, `"forbid"` raise error, `"allow"` keep them |
| `frozen` | Makes model instances immutable/hashable (like a `namedtuple`) |
| `validate_assignment` | By default, Pydantic only validates at creation. Setting this `True` re-validates on `user.age = "not a number"` |
| `from_attributes` | Lets you build a model directly from an object with attributes (e.g., SQLAlchemy ORM row) instead of a dict |
| `str_strip_whitespace` | Cleans string inputs automatically |

### `from_attributes` Example (ORM Integration)

```python
class UserORM:  # e.g., a SQLAlchemy model instance
    def __init__(self, id, name):
        self.id = id
        self.name = name

class UserSchema(BaseModel):
    model_config = ConfigDict(from_attributes=True)
    id: int
    name: str

orm_obj = UserORM(id=1, name="Alice")
schema = UserSchema.model_validate(orm_obj)   # reads .id and .name attributes directly
```

---

## 10. Serialization

Converting a Pydantic model **back** into a dict or JSON string.

```python
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    password: str

user = User(id=1, name="Alice", password="secret123")

# To Python dict
print(user.model_dump())
# {'id': 1, 'name': 'Alice', 'password': 'secret123'}

# To JSON string
print(user.model_dump_json())
# '{"id":1,"name":"Alice","password":"secret123"}'
```

### Excluding / Including Fields

```python
user.model_dump(exclude={"password"})
# {'id': 1, 'name': 'Alice'}

user.model_dump(include={"id", "name"})
# {'id': 1, 'name': 'Alice'}

user.model_dump(exclude_none=True)   # drop fields that are None
user.model_dump(exclude_unset=True)  # only fields explicitly set (not defaults)
user.model_dump(exclude_defaults=True)  # drop fields equal to their default
```

### `exclude` on the Field Itself (e.g., for Passwords)

```python
from pydantic import BaseModel, Field

class User(BaseModel):
    id: int
    name: str
    password: str = Field(exclude=True)   # never included in dump/json output

user = User(id=1, name="Alice", password="secret")
print(user.model_dump())   # {'id': 1, 'name': 'Alice'}  <- password auto-excluded
```

### `by_alias=True`

```python
user.model_dump(by_alias=True)   # uses field aliases instead of Python attribute names
```

> **v1 vs v2 naming (interview trap):** v1 used `.dict()` and `.json()`. v2 renamed these to `.model_dump()` and `.model_dump_json()`. The old methods still work in v2 but are **deprecated**.

---

## 11. Parsing / Deserialization

Multiple ways to build model instances from different input sources.

```python
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str

# From keyword args
u1 = User(id=1, name="Alice")

# From a dict
u2 = User.model_validate({"id": 1, "name": "Alice"})

# From a JSON string
u3 = User.model_validate_json('{"id": 1, "name": "Alice"}')

# From an object with attributes (needs from_attributes=True config)
u4 = User.model_validate(some_orm_object)
```

| Method | Input | Use Case |
|--------|-------|----------|
| `Model(**kwargs)` | keyword args | Direct instantiation |
| `Model.model_validate(obj)` | dict / object | General-purpose parsing |
| `Model.model_validate_json(json_str)` | JSON string | Parsing raw API/file responses |
| `Model.model_construct(**kwargs)` | dict, **skips validation!** | Performance-critical, already-trusted data only |

> **`model_construct()` interview trap:** It creates an instance **without running validation** — useful only when you're 100% sure the data is valid (e.g., loading from your own trusted cache) because it's faster. Misusing it defeats Pydantic's whole purpose.

---

## 12. Computed Fields

Fields derived from other fields, included in serialization output.

```python
from pydantic import BaseModel, computed_field

class Rectangle(BaseModel):
    width: float
    height: float

    @computed_field
    @property
    def area(self) -> float:
        return self.width * self.height

r = Rectangle(width=3, height=4)
print(r.area)                 # 12.0 (accessible like a normal attribute)
print(r.model_dump())         # {'width': 3.0, 'height': 4.0, 'area': 12.0}  <- included!
```

---

## 13. Custom Types & Annotated

### Using `Annotated` for Reusable Constraints

```python
from typing import Annotated
from pydantic import BaseModel, Field

PositiveInt = Annotated[int, Field(gt=0)]

class Product(BaseModel):
    price: PositiveInt
    quantity: PositiveInt
```

### Custom Validators with Annotated + `AfterValidator`

```python
from typing import Annotated
from pydantic import BaseModel, AfterValidator

def must_be_even(v: int) -> int:
    if v % 2 != 0:
        raise ValueError("must be even")
    return v

EvenInt = Annotated[int, AfterValidator(must_be_even)]

class Config(BaseModel):
    batch_size: EvenInt
```

### Built-in Special Types

```python
from pydantic import BaseModel, EmailStr, HttpUrl, SecretStr, PositiveInt, conint, constr

class User(BaseModel):
    email: EmailStr              # validates proper email format (needs `email-validator` pkg)
    website: HttpUrl             # validates proper URL format
    password: SecretStr          # hides value in repr/logs: SecretStr('**********')
    age: PositiveInt             # int > 0
    username: constr(min_length=3, max_length=20)  # constrained string (legacy style, prefer Field)
```

```python
user = User(email="a@b.com", website="https://example.com", password="secret", age=25, username="alice")
print(user.password)          # **********
print(user.password.get_secret_value())  # secret (explicit unwrap needed)
```

---

## 14. Generic Models

Reusable models parameterized by type — very useful for API response wrappers.

```python
from typing import Generic, TypeVar
from pydantic import BaseModel

T = TypeVar("T")

class APIResponse(BaseModel, Generic[T]):
    success: bool
    data: T
    message: str = ""

class User(BaseModel):
    id: int
    name: str

response = APIResponse[User](success=True, data=User(id=1, name="Alice"))
print(response.data.name)   # Alice
```

> **Real-world use:** Wrapping every API response in a consistent `{success, data, message}` shape while keeping `data`'s inner type strictly validated per-endpoint.

---

## 15. Enums in Pydantic

```python
from enum import Enum
from pydantic import BaseModel

class Role(str, Enum):
    ADMIN = "admin"
    USER = "user"
    GUEST = "guest"

class Account(BaseModel):
    username: str
    role: Role

acc = Account(username="alice", role="admin")   # string coerced to Enum member
print(acc.role)              # Role.ADMIN
print(acc.role.value)        # "admin"

Account(username="bob", role="superadmin")  # ❌ ValidationError: not a valid enumeration member
```

> **Why `str, Enum` (not just `Enum`)?** Making it also inherit `str` means it serializes cleanly to JSON as a plain string and behaves like a string in comparisons (`acc.role == "admin"` → `True`).

---

## 16. Union Types & Discriminated Unions

### Basic Union

```python
from typing import Union
from pydantic import BaseModel

class Item(BaseModel):
    value: Union[int, str]      # or: int | str  (Python 3.10+)

Item(value=5)       # ✅ int
Item(value="five")  # ✅ str
```

### Discriminated (Tagged) Unions — Important for Interviews

Used when a field's shape depends on a "type" tag — very common in polymorphic APIs (e.g., different payment methods, different event types).

```python
from typing import Union, Literal
from pydantic import BaseModel, Field

class Cat(BaseModel):
    pet_type: Literal["cat"]
    meow_volume: int

class Dog(BaseModel):
    pet_type: Literal["dog"]
    bark_volume: int

class Owner(BaseModel):
    pet: Union[Cat, Dog] = Field(discriminator="pet_type")

Owner(pet={"pet_type": "cat", "meow_volume": 5})   # ✅ correctly resolves to Cat
Owner(pet={"pet_type": "dog", "bark_volume": 8})   # ✅ correctly resolves to Dog
```

> **Why this matters:** Without a discriminator, Pydantic tries each type in the Union in order ("smart union" matching), which can be slow and sometimes ambiguous. A discriminator makes resolution **instant and unambiguous** — it looks at the tag field first and picks the exact model. This is a favorite senior-level interview question.

---

## 17. Error Handling (ValidationError)

```python
from pydantic import BaseModel, ValidationError

class User(BaseModel):
    id: int
    name: str
    age: int

try:
    User(id="abc", name="Alice", age=-5)
except ValidationError as e:
    print(e.errors())
```

### Structured Error Output

```python
[
    {
        'type': 'int_parsing',
        'loc': ('id',),
        'msg': 'Input should be a valid integer, unable to parse string as an integer',
        'input': 'abc',
        'url': 'https://errors.pydantic.dev/2.x/v/int_parsing'
    },
    {
        'type': 'greater_than',
        'loc': ('age',),
        'msg': 'Input should be greater than 0',
        'input': -5,
        'ctx': {'gt': 0}
    }
]
```

Each error tells you:
- `loc` — exact field path (works for nested fields too, e.g., `('address', 'zip_code')`)
- `msg` — human-readable message
- `type` — machine-readable error code (great for i18n / custom error mapping)
- `input` — the actual bad value received

> **Why this matters for interviews:** This structured format is exactly what FastAPI uses to auto-generate its `422 Unprocessable Entity` responses — a direct link between Pydantic and API error handling.

---

## 18. Settings Management (pydantic-settings)

Validate configuration from **environment variables** / `.env` files with the same type-safety as request data.

```bash
pip install pydantic-settings
```

```python
from pydantic_settings import BaseSettings, SettingsConfigDict

class Settings(BaseSettings):
    model_config = SettingsConfigDict(env_file=".env", env_file_encoding="utf-8")
    
    app_name: str = "MyApp"
    debug: bool = False
    database_url: str
    secret_key: str

settings = Settings()   # automatically reads from environment variables / .env file
print(settings.database_url)
```

### `.env` file example
```
DATABASE_URL=postgresql://user:pass@localhost/db
SECRET_KEY=supersecret
DEBUG=true
```

### Why This Matters
- Environment variables are always **strings** by default — Pydantic coerces `"true"` → `True`, `"5432"` → `5432`, etc.
- Missing required config fails **fast at startup** instead of causing a mysterious `KeyError` deep in your code later.
- Centralizes all config in **one validated, typed object** instead of scattered `os.getenv()` calls.

---

## 19. Pydantic Dataclasses

For when you want dataclass syntax but with Pydantic validation.

```python
from pydantic import field_validator
from pydantic.dataclasses import dataclass

@dataclass
class Point:
    x: int
    y: int

    @field_validator("x")
    @classmethod
    def x_must_be_positive(cls, v):
        if v < 0:
            raise ValueError("x must be positive")
        return v

p = Point(x=1, y=2)   # validated just like BaseModel
```

**Difference from `BaseModel`:** Pydantic dataclasses behave more like standard `@dataclass` (support `__post_init__`, work with other dataclass-based tooling) but still get Pydantic's validation. Use `BaseModel` for most application code; use Pydantic dataclasses when integrating with libraries that expect standard dataclasses.

---

## 20. Pydantic v1 vs v2 (Interview Favorite)

This is one of the **most commonly asked** Pydantic interview questions.

| Aspect | v1 | v2 |
|--------|----|----|
| Core engine | Pure Python | Rust (`pydantic-core`) — 5-50x faster |
| Serialize to dict | `.dict()` | `.model_dump()` |
| Serialize to JSON | `.json()` | `.model_dump_json()` |
| Parse from dict | `.parse_obj()` | `.model_validate()` |
| Parse from JSON | `.parse_raw()` | `.model_validate_json()` |
| Field validator | `@validator` | `@field_validator` |
| Cross-field validator | `@root_validator` | `@model_validator` |
| Config | inner `class Config:` | `model_config = ConfigDict(...)` |
| ORM mode | `orm_mode = True` | `from_attributes=True` |
| Construct without validation | `.construct()` | `.model_construct()` |
| Strict mode | limited | native, per-field or model-wide |
| Computed fields | not built-in | `@computed_field` |
| Discriminated unions | supported, clunkier | first-class support via `Field(discriminator=...)` |

> **Key talking point:** Pydantic v2 wasn't just an API refresh — the validation core was rewritten in **Rust** as a separate package (`pydantic-core`), making it dramatically faster while keeping (mostly) the same Pythonic developer experience. v1 methods still work in v2 as deprecated aliases for backward compatibility, but new code should always use v2 idioms.

---

## 21. Pydantic + FastAPI Integration

This is **the** most common real-world use case, and interviewers often probe this connection.

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class UserCreate(BaseModel):
    name: str
    age: int
    email: str

class UserResponse(BaseModel):
    id: int
    name: str

@app.post("/users", response_model=UserResponse)
async def create_user(user: UserCreate):
    # FastAPI automatically:
    # 1. Parses the incoming JSON body
    # 2. Validates it against UserCreate
    # 3. Returns 422 with structured errors if invalid
    # 4. Gives you a fully validated `user` object with autocomplete
    new_id = 1
    return UserResponse(id=new_id, name=user.name)
```

### What FastAPI Does With Pydantic Under the Hood
1. **Request validation** — request body/query params/path params validated against your Pydantic models
2. **Response validation & filtering** — `response_model` ensures you never leak extra fields (like passwords) accidentally
3. **Automatic OpenAPI/Swagger docs** — generated directly from Pydantic model schemas (`model_json_schema()`)
4. **Dependency injection** — settings (`pydantic-settings`) plug directly into FastAPI's `Depends()`

### Getting JSON Schema (used for Swagger docs)

```python
print(UserCreate.model_json_schema())
```

```json
{
    "title": "UserCreate",
    "type": "object",
    "properties": {
        "name": {"title": "Name", "type": "string"},
        "age": {"title": "Age", "type": "integer"},
        "email": {"title": "Email", "type": "string"}
    },
    "required": ["name", "age", "email"]
}
```

---

## 22. Performance Notes

- Pydantic v2's validation core (`pydantic-core`) is written in **Rust**, compiled to a native extension — this is why v2 is often **5-50x faster** than v1 for validation-heavy workloads.
- `model_construct()` skips validation entirely for performance-critical paths where data is already trusted (use sparingly and only when you're certain).
- Reuse model classes instead of building dynamic models repeatedly — model class creation has overhead (schema building), but instantiation is fast.
- For very large datasets, consider validating once at ingestion rather than per-access.

---

## 23. Common Interview Questions

**Q1: What problem does Pydantic solve that plain Python type hints don't?**
> Plain type hints are just documentation — Python doesn't enforce them at runtime. Pydantic actively validates data against those hints at runtime and raises clear errors, plus provides parsing/serialization.

**Q2: Difference between `Optional[str]` and `str = None`?**
> `Optional[str]` alone still makes the field **required** — you must also supply a default (usually `= None`) to make it truly optional to omit.

**Q3: What's the difference between `@field_validator` and `@model_validator`?**
> `@field_validator` validates a single field in isolation. `@model_validator` runs after (or before) all fields are set and can validate relationships **between** fields (e.g., password confirmation, date ranges).

**Q4: How does Pydantic differ from Python's `dataclasses`?**
> `dataclasses` just reduces boilerplate for classes — no runtime validation, no type coercion, no built-in serialization. Pydantic adds full runtime validation, coercion, JSON schema generation, and serialization on top of a similar declarative syntax.

**Q5: What is a discriminated union and why use one?**
> A Union type where a "tag" field (`Literal[...]`) tells Pydantic exactly which model variant to use, instead of trying each type in order. Faster and unambiguous — critical for polymorphic APIs (e.g., different event/payload types).

**Q6: How would you exclude a sensitive field like `password` from API responses?**
> Either use a separate response model that doesn't include the field, or use `Field(exclude=True)` on the model used for input to strip it from `model_dump()`/`model_dump_json()` output.

**Q7: What does `from_attributes=True` (formerly `orm_mode`) do?**
> Allows a Pydantic model to be built directly from an object's **attributes** (like an ORM row) instead of requiring a dict — used heavily when converting SQLAlchemy models to API response schemas.

**Q8: Why is Pydantic v2 faster than v1?**
> The validation core was rewritten in Rust (`pydantic-core`), replacing the pure-Python validation logic of v1.

**Q9: How does Pydantic integrate with FastAPI specifically?**
> FastAPI uses Pydantic models to validate request bodies/params, filter/validate response data via `response_model`, and auto-generate OpenAPI/Swagger documentation from the models' JSON schema.

**Q10: What happens if extra/unexpected fields are passed to a model?**
> By default (`extra="ignore"`), they're silently dropped. You can configure `extra="forbid"` to raise a validation error instead, or `extra="allow"` to keep them accessible.

---

## 24. Cheat Sheet

```python
from pydantic import (
    BaseModel, Field, field_validator, model_validator,
    ConfigDict, ValidationError, computed_field,
    EmailStr, HttpUrl, SecretStr
)

class Example(BaseModel):
    model_config = ConfigDict(
        extra="forbid",
        str_strip_whitespace=True,
        validate_assignment=True,
        from_attributes=True,
    )

    id: int
    name: str = Field(min_length=1, max_length=100)
    email: EmailStr
    age: int | None = Field(default=None, ge=0, le=120)
    tags: list[str] = Field(default_factory=list)

    @field_validator("name")
    @classmethod
    def clean_name(cls, v):
        return v.strip().title()

    @model_validator(mode="after")
    def check_something(self):
        return self

    @computed_field
    @property
    def display_name(self) -> str:
        return f"{self.name} <{self.email}>"


# Creation
obj = Example(id=1, name="alice", email="a@b.com")
obj = Example.model_validate({"id": 1, "name": "alice", "email": "a@b.com"})
obj = Example.model_validate_json('{"id":1,"name":"alice","email":"a@b.com"}')

# Serialization
obj.model_dump()
obj.model_dump_json()
obj.model_dump(exclude={"email"})
obj.model_dump(exclude_none=True)

# Schema
Example.model_json_schema()

# Error handling
try:
    Example(id="bad", name="", email="not-an-email")
except ValidationError as e:
    print(e.errors())
```

### Quick Method Name Reference (v2)

| Action | Method |
|--------|--------|
| Create from dict | `Model.model_validate(data)` |
| Create from JSON string | `Model.model_validate_json(json_str)` |
| Create without validation | `Model.model_construct(**data)` |
| To dict | `instance.model_dump()` |
| To JSON string | `instance.model_dump_json()` |
| Get JSON Schema | `Model.model_json_schema()` |
| Copy with changes | `instance.model_copy(update={...})` |
| Get set fields only | `instance.model_fields_set` |

---

## 🎯 Final Revision Checklist

- [ ] Explain the core problem Pydantic solves (untyped runtime data)
- [ ] Basic `BaseModel` creation & type coercion behavior
- [ ] `Field()` constraints (`gt`, `ge`, `min_length`, `pattern`, etc.)
- [ ] `default_factory` vs plain `default` (mutable default bug)
- [ ] `Optional[X]` vs actually optional (needs `= None`)
- [ ] Nested models & validation error paths
- [ ] `@field_validator` (before/after mode) vs `@model_validator`
- [ ] `ConfigDict` options: `extra`, `frozen`, `from_attributes`, `validate_assignment`
- [ ] `model_dump()` / `model_dump_json()` with `exclude`/`include`
- [ ] `model_validate()` / `model_validate_json()` / `model_construct()`
- [ ] `@computed_field`
- [ ] Discriminated unions with `Literal` + `Field(discriminator=...)`
- [ ] `ValidationError.errors()` structure
- [ ] `pydantic-settings` for env var / `.env` config validation
- [ ] Full v1 → v2 method name mapping
- [ ] How FastAPI uses Pydantic (request/response/docs)

---

> **Good luck with your interview & development work! 🚀**
> *Pydantic's core value prop in one line: "Type hints become runtime guarantees."*
