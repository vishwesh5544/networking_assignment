
# Awesome Web Deployment

This documentation provides the steps to deploy a website on localhost using Nginx with the DNS name 'awesomeweb'. The deployment is done on a Linux Pop!_OS system using Neovim as the text editor.
Link to my Neovim config: [Neovish](https://github.com/vishwesh5544/neovish)

## Nginx Configuration

The Nginx configuration for `awesomeweb` is as follows:

```
server {
    listen 80;
    server_name awesomeweb;

    root /var/www/html/awesomeweb;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

## HTML Content

The `index.html` for `awesomeweb` is as follows:

```
<!DOCTYPE html>
<html>
<head>
    <title>Welcome to Awesome Web</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 20px 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            text-align: center;
            background: white;
            padding: 40px 20px;
            margin: 20px 0;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 80%;
            max-width: 800px;
        }
        h1 {
            color: #333;
        }
        p {
            color: #666;
        }
        .content {
            margin-top: 20px;
            text-align: left;
        }
        .content h2 {
            color: #444;
        }
        .content ul {
            list-style-type: none;
            padding: 0;
        }
        .content ul li {
            background: #eee;
            margin: 5px 0;
            padding: 10px;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Welcome to Awesome Web!</h1>
        <p>Created by Vishwesh Shukla</p>
        <div class="content">
            <h2>About Me</h2>
            <p>Vishwesh Shukla is an accomplished and results-oriented Software Engineer with a comprehensive background in developing and deploying enterprise-grade software solutions across various sectors, including media, e-commerce, and IT services.</p>
            
            <h2>Key Competencies</h2>
            <ul>
                <li>Software Design</li>
                <li>Frontend Development</li>
                <li>Mobile App Development</li>
                <li>Backend Development</li>
                <li>API Development</li>
                <li>Database Design</li>
                <li>AWS Cloud</li>
                <li>Java</li>
                <li>Flutter</li>
                <li>Kotlin (Spring Boot, Ktor)</li>
            </ul>
            
            <h2>Professional Experience</h2>
            <p><strong>Tezda Pvt Ltd:</strong> Senior Software Developer (Remote)</p>
            <p><strong>Tellygence Technology, UK:</strong> Software Engineer (Remote)</p>
            <p><strong>JobCommand:</strong> Lead Software Engineer (Remote)</p>
            <p><strong>Anglia Ruskin University, Cambridge, UK:</strong> Customer Service Agent, IT Desk</p>
            <p><strong>Grapple Software and Outsourcing Pvt Ltd:</strong> Senior Software Developer (Remote)</p>

            <h2>Contact</h2>
            <p>If you have any questions or feedback, feel free to contact me at <a href='mailto:vishweshshukla20@gmail.com'>vishweshshukla20@gmail.com</a>.</p>
        </div>
    </div>
</body>
</html>
```

## Steps Involved

1. **Install Nginx**:
    ```
    sudo apt update
    sudo apt install nginx
    ```

2. **Create HTML Directory**:
    ```
    sudo mkdir -p /var/www/html/awesomeweb
    sudo chown -R $USER:$USER /var/www/html/awesomeweb
    ```

3. **Place `index.html` in the Directory**:
    ```
    sudo nano /var/www/html/awesomeweb/index.html
    ```

4. **Edit Nginx Configuration**:
    ```
    sudo nano /etc/nginx/sites-available/awesomeweb
    ```

    Place the above Nginx configuration in the file.

5. **Enable the Configuration**:
    ```
    sudo ln -s /etc/nginx/sites-available/awesomeweb /etc/nginx/sites-enabled/
    ```

6. **Test Nginx Configuration**:
    ```
    sudo nginx -t
    ```

7. **Restart Nginx**:
    ```
    sudo systemctl restart nginx
    ```

8. **Update Hosts File**:
    ```
    sudo nano /etc/hosts
    ```

    Add the following line:
    ```
    127.0.0.1 awesomeweb
    ```

9. **Access the Website**:
    Open a browser and navigate to `http://awesomeweb`.

## Note

This setup is done on Linux Pop!_OS using Neovim as the text editor.

## Contact

For any issues or questions, contact Vishwesh Shukla at <vishweshshukla20@gmail.com>.
