# FalconArch Framework

**Você fala português? Leia o README em Português _[aqui](https://github.com/celiovmjr/falcon-arch/blob/main/README.md)_**

**FalconArch** is a lightweight and modular library that provides a base framework for developing applications with **Flask**. It simplifies the creation of routes, blueprint management, and dynamic controller loading, as well as supporting multiple HTTP methods and providing detailed logs to make debugging easier.

## 🚀 Features

- **MVC-based structure**: Organize your application modularly using the **Model-View-Controller** pattern.
- **Simplified blueprint registration**: Easily register controllers and routes with a simple interface.
- **Dynamic controller loading**: Automatically load controllers without the need for complex configurations.
- **Support for multiple HTTP methods**: Define routes for different HTTP methods (`GET`, `POST`, `PUT`, `DELETE`, etc.).
- **Detailed logs with emojis**: The framework provides logs with emojis to make the debugging process easier and more intuitive.

## 📂 Project Structure

```
.
├── app
│   ├── models
│   │   └── ...
│   ├── views
│   │   └── ...
│   ├── http
│   │   ├── middlewares
│   │   │   └── ...
│   │   ├── requests
│   │   │   └── ...
│   │   └── controllers
│   │       └── ...
│   └── services
│       └── ...
├── public
│   └── ...
└── routes
    └── ...
```

## 🛠 Installation

```bash
pip install falcon-arch
```

## 🎨 How to Declare Routes

### **Defining Routes in Files**:

- **Example route for a web page**:

   ```python
   from falcon_arch import Router

   web = Router()

   web.get("/home", "HomeController@index")
   web.post("/submit", "FormController@submit")
   ```

- **Example route for an API**:

   ```python
   from falcon_arch import Router

   users = Router(prefix="/api/users")

   users.get("/", "UserController@index")
   users.get("/<int:id>", "UserController@show")
   users.post("/", "UserController@store")
   ```

### **Registering Routes in the Server**:

```python
from falcon_arch import FalconArch

app = FalconArch(__name__, template_folder="app/views", static_folder="public")

if __name__ == "__main__":
    app.run(app, host="0.0.0.0", port=80, threads=10, _quiet=True)
```

## 📜 Rendering Views

To render a view using **Jinja**, use the `Response.render` method:

```python
from falcon_arch import Response

def index(request, response: Response):
    return response.render("home.html", {"title": "Home Page"})
```

The default directory for views is `/app/views`, and static files are located in `/public`.

---

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for more details.

---

### 🔧 Logs and Debugging

**FalconArch** provides detailed and interactive logs with emojis, making it easier to track what is happening in the application. This helps to debug errors more efficiently and in a more user-friendly way.