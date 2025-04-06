# virtualenv
### 🔍 What is virtualenv?
virtualenv is a tool that lets you create isolated Python environments. This means you can have separate sets of Python packages for different projects without conflicts.

1. Install virtualenv:
   ```bash
   pip install your-package-name
   ```

2. Create a virtual environment:
   ```bash
   python -m virtualenv venv
   ```

3. Activate the virtual environment:
   - On Windows:
      ```bash
      venv\Scripts\activate
      ```
   - On macOS/Linux:
     ```bash
      source venv/bin/activate
      ```
4. Deactivate it when you're done:
   ```bash
      deactivate
   ```

# Django
1. Install Django:
   ```bash
   pip install django
   ```
   
2. Create a new Django project named  ```firstweb ```:
   ```bash
   django-admin startproject firstweb
   ```
   Breaking it down:
   - ```django-admin```: A command-line utility provided by Django to perform various tasks like creating projects, apps, etc.
   - ```startproject```: A subcommand that tells Django to set up the basic structure for a new project.
   - ```firstweb```: The name of my new project.
