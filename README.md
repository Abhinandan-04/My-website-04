<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Website</title>
    <style>
        /* Your CSS styles here */
        body {
    font-family: 'Arial', sans-serif;
    background-color: #f8f8f8;
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
}

.login-container {
    background-color: #ffffff;
    padding: 30px;
    border-radius: 8px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    width: 300px;
}

.login-container h2 {
    text-align: center;
    color: #333333;
}

.login-form {
    display: flex;
    flex-direction: column;
}

.form-group {
    margin-bottom: 20px;
}

.form-group label {
    font-weight: bold;
    margin-bottom: 8px;
    color: #555555;
}

.form-group input {
    width: 100%;
    padding: 10px;
    box-sizing: border-box;
    border: 1px solid #cccccc;
    border-radius: 4px;
}

.form-group input[type="submit"] {
    background-color: #4caf50;
    color: white;
    cursor: pointer;
}

.form-group input[type="submit"]:hover {
    background-color: #45a049;
}

a {
    color: #3498db;
    text-decoration: none;
}

a:hover {
    color: #2574a9;
}

    </style>
</head>
<body>

<div id="content">
    <!-- Default content, dynamically changed by JavaScript -->
    <h2>Welcome to the Simple Website!</h2>
</div>

<script>
    // Initial content
    document.getElementById("content").innerHTML = `
        <h2>Welcome to the Simple Website!</h2>
        <p>This is the default content. Navigate using the links above.</p>
    `;

    // Sample user credentials (in a real scenario, use server-side validation)
    const users = [
        { username: "noob", password: "bot" },
        { username: "noob", password: "bot" }
    ];

    function showLogin() {
        document.getElementById("content").innerHTML = `
            <h2>Login</h2>
            <form onsubmit="return validateLogin()">
                <div>
                    <label for="username">Username:</label>
                    <input type="text" id="username" name="username" required>
                </div>
                <div>
                    <label for="password">Password:</label>
                    <input type="password" id="password" name="password" required>
                </div>
                <div>
                    <input type="submit" value="Login">
                </div>
            </form>
            <p>Don't have an account? <a href="#" onclick="showRegistration()">Register here</a>.</p>
        `;
    }

    function validateLogin() {
        var username = document.getElementById("username").value;
        var password = document.getElementById("password").value;

        // Check if the entered credentials are valid
        var isValid = users.some(user => user.username === username && user.password === password);

        if (isValid) {
            document.getElementById("content").innerHTML = `
                <h2>Welcome, ${username}!</h2>
                <p>You have successfully logged in.</p>
                <p><a href="#" onclick="showLogin()">Logout</a>.</p>
            `;
        } else {
            alert("Invalid username or password. Please try again.");
        }

        // Prevent the form from submitting
        return false;
    }

    function showRegistration() {
        document.getElementById("content").innerHTML = `
            <h2>Registration</h2>
            <form onsubmit="return registerUser()">
                <div>
                    <label for="newUsername">New Username:</label>
                    <input type="text" id="newUsername" name="newUsername" required>
                </div>
                <div>
                    <label for="newPassword">New Password:</label>
                    <input type="password" id="newPassword" name="newPassword" required>
                </div>
                <div>
                    <input type="submit" value="Register">
                </div>
            </form>
            <p>Already have an account? <a href="#" onclick="showLogin()">Login here</a>.</p>
        `;
    }

    function registerUser() {
        var newUsername = document.getElementById("newUsername").value;
        var newPassword = document.getElementById("newPassword").value;

        // Check if the username is already taken
        if (users.some(user => user.username === newUsername)) {
            alert("Username already taken. Please choose another.");
        } else {
            // Add the new user to the list
            users.push({ username: newUsername, password: newPassword });
            alert("Registration successful! You can now log in with your new credentials.");
            showLogin(); // Redirect to the login page
        }

        // Prevent the form from submitting
        return false;
    }
</script>

<nav>
    <ul>
        <li><a href="#" onclick="showLogin()">Login</a></li>
        <li><a href="#" onclick="showRegistration()">Register</a></li>
    </ul>
</nav>

</body>
</html>

