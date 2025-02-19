---

### PATCH: Partially Update an Existing Resource

**Example:** Update just the email of a user

```bash
curl -X PATCH "https://api.example.com/users/3" \
  -H "Content-Type: application/json" \
  -d '{"email": "charles.new@example.com"}'
```

**Sample Response:**

```json
{ "id": 3, "name": "Charles", "email": "charles.new@example.com" }
```

---