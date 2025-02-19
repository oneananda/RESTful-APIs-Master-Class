
---

### POST: Create a New Resource

**Example:** Create a new user

```bash
curl -X POST "https://api.example.com/users" \
  -H "Content-Type: application/json" \
  -d '{"name": "Charlie", "email": "charlie@example.com"}'
```

**Sample Response:**

```json
{ "id": 3, "name": "Charlie", "email": "charlie@example.com" }
```

---