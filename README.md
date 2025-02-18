# TextProc

Toy REST API for basic text processing

This was made as a weekend project to learn Flask and basic NLP.

It's a Flask RESTful API with CRUD capabilities that can also do some basic text processing.

- Using SQLAlchemy and Flask-Marshmallow for DB
- Flask-RESTful for the actual REST resources
- And simple text processing functions that use NLTK.

### Create env

```bash
conda env create -f environment.yml
```

```python
import nltk

nltk.download('punkt_tab')
nltk.download('stopwords')
nltk.download('wordnet')
```

### Init db and run api:

```
uvicorn src.app:app --reload
```

### Usage examples (cURL):

- Create new user:

```
curl -X POST http://127.0.0.1:8000/users \
     -H "Content-Type: application/json" \
     -d '{"name":"João","content":"I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system, and expound the actual teachings of the great explorer of the truth, the master-builder of human happiness."}'
```

- Get user 1's bag-of-words:

```
curl --header "Content-Type: application/json" --request GET  http://localhost:8000/users/1/getbow
```

- Get the word most similar to 'pleasure' in user 1's vocabulary:

```
curl -X POST http://127.0.0.1:8000/users/1/wordvec \
     -H "Content-Type: application/json" \
     -d '{"word": "pleasure"}'
```
