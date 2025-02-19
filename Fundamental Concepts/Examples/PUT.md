
---

### PUT: Update an Existing Resource Entirely

**Example:** Update an entire user record

```bash
curl -X PUT "https://api.example.com/users/3" \
  -H "Content-Type: application/json" \
  -d '{"name": "Charles", "email": "charles@example.com"}'
```

**Sample Response:**

```json
{ "id": 3, "name": "Charles", "email": "charles@example.com" }
```

---