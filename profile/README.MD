
# 🚀 MicroJet - Modern Python Web Framework

[![Python 3.7+](https://img.shields.io/badge/python-3.7%2B-blue)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status: Alpha](https://img.shields.io/badge/Status-Alpha-orange)]()

> Python web framework with a lightweight, fast, and React-like component system

```
         🌟 MicroJet Framework
NOTE: This project is under construction.
so please don't use it now.
(We will let you know when
it will be available here.)            

```

## 📋 Content

- [Features](#-বৈশিষ্ট্য)
- [Quick start](#-দ্রুত-শুরু)
- [CLI commands](#-cli-কমান্ড)
- [Examples](#-উদাহরণ)
- [Architecture](#-আর্কিটেকচার)
- [Documentation](#-ডকুমেন্টেশন)

---

## ✨ Features

### 🎯 Key Benefits

- **Easy Routing** - Decorator-based system like Bottle.py
- **React-like components** - reusable, recompilable UI components
- **Built-in component library** - Button, Card, Form, NavBar, Alert etc.
- **Powerful CLI** - Project and Component Management
- **Static file support** - CSS, JavaScript, image serving
- **No dependencies** - just the Python standard library!
- **Rapid Development** - Create prototypes quickly
- **Easy Deployment** - WSGI compatible

---

## 🚀 Quick start

### Step 1: Download the file

```bash
# Download the original files
# - microjet_core.py
# - jet (CLI tool)
```

### Step 2: Create a new project

```bash
./jet new my_awesome_app
cd my_awesome_app
```

This will create the following structure:
```
my_awesome_app/
├── app.py # Main application
├── components/ # Reusable components
├── static/ # CSS, JS, images
├── jet.json # Project configuration
└── README.md # Project documentation
```

### Step 3: Install components (Optional)

```bash
./jet install button
./jet install card
./jet install form
./jet install navbar
./jet install alert
```

### Step 4: Run the development server

```bash
./jet run
```

Open in your browser: **http://localhost:8000** 🎉

---

## 📱 CLI commands

```bash
jet new <project_name> # Create a new project
jet install <component>   # Install the component
jet run # Run the development server
jet list # View all components
jet --help # Get help
```

### Examples

```bash
# Create a new blog project
$ jet new my_blog

# Go to project
$ cd my_blog

# Install the component
$ jet install navbar
$ jet install card

# Run the server
$ jet run
```

---

## 💡 Example

### Simple "Hello World" app

```python
from microjet_core import MicroJet, h1, div

app = MicroJet("Hello App")

@app.route("/")
def home():
    page = div()
    title = h1()
    title.add_child("Hello, MicroJet! 👋")
    page.add_child(title)
    return f"<!DOCTYPE html><html><body>{page.to_html()}</body></html>"

if __name__ == "__main__":
    app.run()
```

### Route with parameters

```python
@app.route("/greet/:name")
def greet(name):
    page = div()
    msg = h1()
    msg.add_child(f"Hello, {name}!")
    page.add_child(msg)
    return f"<!DOCTYPE html><html><body>{page.to_html()}</body></html>"

# Go to browser: http://localhost:8000/greet/Ali
```

### Create custom components

```python
# components/welcome.py
from microjet_core import HtmlComponent

class WelcomeCard(HtmlComponent):
    def __init__(self, name, props=None):
        super().__init__("div", props or {"className": "welcome-card"})
        self.name = name
    
    def render(self):
        title = HtmlComponent("h2")
        title.add_child(f"Welcome, {self.name}!")
        self.add_child(title)
        return self

# app.py
from components.welcome import WelcomeCard

@app.route("/")
def home():
    card = WelcomeCard("Abdul")
    card.render()
    return f"<!DOCTYPE html><html><body>{card.to_html()}</body></html>"
```

### API endpoint

```python
@app.route("/api/users")
def get_users():
    return {
        "users": [
            {"id": 1, "name": "Ali"},
            {"id": 2, "name": "Fatima"}
        ]
    }

# Access http://localhost:8000/api/users
# Get JSON response
```

---

## 🏗️ Architecture

### File structure

```
MicroJet/
├── microjet_core.py # Core framework (~250 lines)
├── jet # CLI tool (~350 lines)
├── MICROJET_DOCS.md # Detailed documentation
├── INSTALLATION.md # Installation Guide
├── example_blog_app.py # Complete blog example
├── setup.py # Package setup
└── README.md # This file
```

### Core component

#### 1. **Component Class** - Base Class
```python
class Component:
    - render() # Render
    - to_html() # Convert to HTML
    - add_child() # Add child
    - set_prop() # Set property
```

#### 2. **HtmlComponent** - HTML component
```python
class HtmlComponent(Component):
    - tag # HTML tags (div, p, h1, etc.)
    - props # HTML attribute
    - children # Child elements
```

#### 3. **MicroJet Class** - Main Application
```python
class MicroJet:
    - route() # Register route
    - run() # Run the server
    - register_component() # Register the component
    - static() # Serve static files
```

---

## 📚 Documentation

### File Guide

| File | Description |
|------|-------|
| `MICROJET_DOCS.md` | Full documentation and API reference |
| `INSTALLATION.md` | Installation and Setup Guide |
| `example_blog_app.py` | A fully working blog application |

### Quick reference

```python
# Route registration
@app.route("/")
@app.route("/user/:name")
@app.route("/post/:id", methods=["GET", "POST"])

# Component creation
from microjet_core import div, p, h1, button, form

# Component usage
component.add_child(child)
component.set_prop("className", "my-class")
component.to_html()
```

---

## 🎓 Learning Resources

### For beginners
1. Read this README
2. `example_blog_app.py` Invoice
3. `INSTALLATION.md` Follow

### For intermediate users
1. `MICROJET_DOCS.md` Read all parts of it.
2. Create your own component
3. Add API endpoint

### For advanced users
1. `microjet_core.py` Analyze its code
2. Write custom middleware
3. Create your own component library

---

## 🛠️ Pre-built components

Components that come with MicroJet:

```
button - clickable button component
card - Content card component
form - Form and field components
navbar - Navigation bar component
alert - Notification alert component
```

Each pre-built component is fully customizable and can be styled.

---

## 🌍 Real world use

With MicroJet you can create:

- 📝 **Blog Platform** - See example
- 🛒 **E-Commerce Site** - Product Listing and Cart
- 📊 **Dashboard** - Real-time data visualization
- 💬 **Social Network** - Post and Comment System
- 🎓 **Education Platform** - Course Management
- 🎮 **Gaming Portal** - Leaderboards and Profiles

---

## 💻 System Requirements

- **Python** 3.7 or above
- **OS** - Linux, macOS, Windows all supported
- **Disk** - Only ~50 KB
- **Memory** - Minimum

**No external dependencies required!**

---

## 📊 Comparison

| Feature | Flask | Bottle | FastAPI | MicroJet |
|------|------|-------|--------|---------|----------|
| Simplicity | ⭐⭐ |
| Component System | ❌ | ❌ | ❌ | ✅ |
| Dependency | Many | Few | Few | 0️⃣ |
| Easy to learn | ⭐ | ⭐⭐⭐⭐⭐ |
| Rapid Prototyping | ⭐⭐ |

---

## 🤝 Contributions and Support

### You can contribute:
- 🐛 Report a bug
- 💡 Suggest new features
- 📝 Improve documentation
- 🧩 Create new component
- 🌍 Contribute to translations

### To get help:
- 📖 Read the documentation
- 💬 Open an issue
- 🔗 Join the discussion

---

## 📄 License

MIT License - Complete freedom!

You can do whatever you want:
- ✅ Use
- ✅ Change
- ✅ Deliver
- ✅ Commercial use

No restrictions!

---

## 🎉 Next steps

1. **Get Started**: `jet new myapp` and `jet run`
2. **Learn**: Read the documentation and try the examples
3. **Create**: Create your own project
4. **Share**: Share your creation with the world
5. **Contribute**: Help the community

---

## 🌟 Special thanks

This project was inspired by

- By the component architecture of **React.js**
- By the flexibility of **Python**

---

## 📞 Contact

- 📧 Email: dev@microjet.dev
- 🐦 Twitter: @microjetdev
- 💬 Discord: MicroJet Community
- 🌐 Website: https://microjet.dev

---
## Contributor
<a href="https://github.com/codegear-2011/MicroJet/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=codegear-2011/MicroJet" />
</a>
---
<div align="center">

### 🚀 Build your next big project with MicroJet!

**Simple. Powerful. Delightful.**

![Status](https://img.shields.io/badge/Status-Active-green?style=for-the-badge)
![Made with](https://img.shields.io/badge/Made%20with-%F0%9F%92%9C%20Python-blue?style=for-the-badge)

</div>
