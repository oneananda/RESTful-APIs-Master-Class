
## Python with Flask

### Prerequisites
- Python installed
- Flask installed (via pip)

### Setup Instructions
1. **Create and activate a virtual environment (optional but recommended):**
   ```bash
   mkdir flask-api
   cd flask-api
   python -m venv venv
   source venv/bin/activate   # For Windows: venv\Scripts\activate
   ```

2. **Install Flask:**
   ```bash
   pip install Flask
   ```

3. **Create `app.py`:**
   ```python
   from flask import Flask, request, jsonify, abort

   app = Flask(__name__)

   # Sample data
   users = [
       {"id": 1, "name": "Alice"},
       {"id": 2, "name": "Bob"}
   ]

   # GET: Retrieve all users
   @app.route('/users', methods=['GET'])
   def get_users():
       return jsonify(users)

   # GET: Retrieve a user by ID
   @app.route('/users/<int:user_id>', methods=['GET'])
   def get_user(user_id):
       user = next((u for u in users if u['id'] == user_id), None)
       if user is None:
           abort(404, description="User not found")
       return jsonify(user)

   # POST: Create a new user
   @app.route('/users', methods=['POST'])
   def create_user():
       new_user = {
           "id": users[-1]['id'] + 1 if users else 1,
           "name": request.json.get('name')
       }
       users.append(new_user)
       return jsonify(new_user), 201

   # PUT: Update an existing user entirely
   @app.route('/users/<int:user_id>', methods=['PUT'])
   def update_user(user_id):
       user = next((u for u in users if u['id'] == user_id), None)
       if user is None:
           abort(404, description="User not found")
       user['name'] = request.json.get('name')
       return jsonify(user)

   # DELETE: Remove a user
   @app.route('/users/<int:user_id>', methods=['DELETE'])
   def delete_user(user_id):
       global users
       users = [u for u in users if u['id'] != user_id]
       return jsonify({"message": "User deleted successfully"})

   if __name__ == '__main__':
       app.run(debug=True, port=5000)
   ```

4. **Run your server:**
   ```bash
   python app.py
   ```
   Your Flask API server will now be running on port 5000.

---