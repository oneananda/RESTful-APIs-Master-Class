
## Node.js with Express

### Prerequisites
- Node.js and npm installed

### Setup Instructions
1. **Initialize your project:**
   ```bash
   mkdir express-api
   cd express-api
   npm init -y
   ```

2. **Install Express:**
   ```bash
   npm install express
   ```

3. **Create `index.js`:**
   ```javascript
   const express = require('express');
   const app = express();

   // Middleware to parse JSON bodies
   app.use(express.json());

   // Sample data
   let users = [
     { id: 1, name: 'Alice' },
     { id: 2, name: 'Bob' }
   ];

   // GET: Retrieve all users
   app.get('/users', (req, res) => {
     res.json(users);
   });

   // GET: Retrieve a user by ID
   app.get('/users/:id', (req, res) => {
     const user = users.find(u => u.id === parseInt(req.params.id));
     if (!user) return res.status(404).json({ error: 'User not found' });
     res.json(user);
   });

   // POST: Create a new user
   app.post('/users', (req, res) => {
     const newUser = {
       id: users.length + 1,
       name: req.body.name
     };
     users.push(newUser);
     res.status(201).json(newUser);
   });

   // PUT: Update an existing user entirely
   app.put('/users/:id', (req, res) => {
     let user = users.find(u => u.id === parseInt(req.params.id));
     if (!user) return res.status(404).json({ error: 'User not found' });
     user.name = req.body.name;
     res.json(user);
   });

   // DELETE: Remove a user
   app.delete('/users/:id', (req, res) => {
     users = users.filter(u => u.id !== parseInt(req.params.id));
     res.json({ message: 'User deleted successfully' });
   });

   // Start the server
   const PORT = process.env.PORT || 3000;
   app.listen(PORT, () => {
     console.log(`Server running on port ${PORT}`);
   });
   ```

4. **Run your server:**
   ```bash
   node index.js
   ```
   Your Express API server should now be running on port 3000.

---