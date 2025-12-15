---
name: api-tester
description: Test REST, GraphQL, and gRPC APIs. Generate automated test suites, perform load testing, validate responses, and monitor API performance. Use when testing APIs, validating endpoints, or checking API health.
allowed-tools: Bash, Read, Grep, Glob
---

# API Tester

Comprehensive API testing toolkit with automated test generation, performance monitoring, and response validation.

## What this Skill does

- Create and execute API test suites
- Support for REST, GraphQL, and gRPC APIs
- Automated test generation from OpenAPI/Swagger specs
- Performance benchmarking and load testing
- Response validation against JSON schemas
- Authentication handling (OAuth, API keys, JWT)
- Detailed test reports (HTML, JSON, JUnit)
- Mock server creation for testing

## Requirements

Install required packages:
```bash
pip install requests httpx jsonschema
pip install pytest pytest-html

# For GraphQL
pip install gqlc

# For load testing
pip install locust

# For OpenAPI
pip install prance
```

## How to use

### Basic API test
```python
import requests

response = requests.get('https://api.example.com/users')

# Assertions
assert response.status_code == 200
assert 'application/json' in response.headers['content-type']
data = response.json()
assert len(data) > 0
print(f"Found {len(data)} users")
```

### Test with authentication
```python
import requests

# API Key
headers = {'Authorization': 'Bearer YOUR_TOKEN'}
response = requests.get('https://api.example.com/protected', headers=headers)

# OAuth2
session = requests.Session()
session.auth = OAuth2Session(client_id='YOUR_ID')
token = session.fetch_token('https://api.example.com/oauth/token')
```

### Load testing with Locust
```python
from locust import HttpUser, task, between

class APIUser(HttpUser):
    wait_time = between(1, 3)

    @task
    def get_users(self):
        self.client.get('/users')

    @task
    def create_user(self):
        self.client.post('/users', json={'name': 'Test User'})
```

### Run tests
```bash
# Run all tests
pytest tests/ --html=report.html

# Run with coverage
pytest --cov=src tests/

# Load test
locust -f load_test.py --host=https://api.example.com
```

### Validate response schema
```python
import requests
import jsonschema

response = requests.get('https://api.example.com/user/123')
data = response.json()

schema = {
    "type": "object",
    "properties": {
        "id": {"type": "integer"},
        "name": {"type": "string"},
        "email": {"type": "string", "format": "email"}
    },
    "required": ["id", "name", "email"]
}

jsonschema.validate(data, schema)
```

## Examples

When to use this Skill:
- "Test this REST API endpoint"
- "Generate test cases from OpenAPI spec"
- "Run load tests on my API"
- "Validate API responses against schema"
- "Create automated test suite"
- "Monitor API performance"

## Test Suite Structure

Create a test suite file:
```python
# tests/test_api.py
import pytest
import requests

BASE_URL = "https://api.example.com"

class TestUserAPI:
    def test_get_users(self):
        response = requests.get(f"{BASE_URL}/users")
        assert response.status_code == 200

    def test_create_user(self):
        data = {"name": "John", "email": "john@example.com"}
        response = requests.post(f"{BASE_URL}/users", json=data)
        assert response.status_code == 201

    def test_get_user(self):
        response = requests.get(f"{BASE_URL}/users/1")
        assert response.status_code == 200
        assert 'id' in response.json()
```

## Tips

- Use environment variables for API URLs and credentials
- Implement retry logic for flaky tests
- Log detailed information for debugging
- Use data-driven tests for multiple scenarios
- Mock external dependencies in unit tests
