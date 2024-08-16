# sivamuthu01 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Card Grid with Inline Scripting</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        nav {
            background-color: #333;
            color: white;
            padding: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .brand {
            font-size: 24px;
        }
        button {
            background-color: #28a745;
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        .user-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
            padding: 20px;
        }
        .user-card {
            background: white;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            padding: 20px;
            text-align: center;
        }
        .user-card img {
            border-radius: 50%;
            width: 100px;
            height: 100px;
            margin-bottom: 15px;
        }
        .loader {
            display: none;
            border: 5px solid #f3f3f3;
            border-radius: 50%;
            border-top: 5px solid #333;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <nav>
        <div class="brand">MyBrand</div>
        <button onclick="
            document.getElementById('loader').style.display = 'block';
            document.getElementById('userGrid').innerHTML = '';
            fetch('https://reqres.in/api/users?page=1')
                .then(response => response.json())
                .then(data => {
                    document.getElementById('loader').style.display = 'none';
                    data.data.forEach(user => {
                        document.getElementById('userGrid').innerHTML += `
                            <div class='user-card'>
                                <img src='${user.avatar}' alt='${user.first_name}'>
                                <h3>${user.first_name} ${user.last_name}</h3>
                                <p>${user.email}</p>
                            </div>`;
                    });
                })
                .catch(error => {
                    document.getElementById('loader').style.display = 'none';
                    alert('Failed to fetch users. Please try again later.');
                    console.error(error);
                });
        ">Get Users</button>
    </nav>
    <div id="loader" class="loader"></div>
    <div id="userGrid" class="user-grid"></div>
</body>
</html>

This project teaches core web development skills, including HTML structure, CSS styling, and JavaScript interactivity. It also introduces the concept of deploying a web app so that others can use it, which is an important skill in web development
