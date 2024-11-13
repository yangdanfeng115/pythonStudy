**To install Python on Windows, follow these steps:**

# **Step 1: Download the Python Installer**

Open your web browser and visit the official Python website: https://www.python.org/

On the homepage, click the Downloads button. It will automatically detect your operating system (Windows) and recommend the latest version of Python for you.

Alternatively, you can go to Downloads > Windows to see a list of versions and download a specific one.

# **Step 2: Run the Python Installer**

Once the installer file (.exe) is downloaded, double-click on it to run it.

On the installation screen, important step: check the box that says "Add Python to PATH". This ensures that Python and pip (Python's package installer) are accessible from the command line (Command Prompt or PowerShell).

If you don't check this box, you'll need to manually add Python to your system's PATH environment later, which can be more complicated.

After selecting "Add Python to PATH," click Install Now.

Wait for the installation to complete. It should only take a few minutes.

# **Step 3: Verify the Installation**

Once the installation is complete, you need to verify that Python was installed correctly:

Open Command Prompt:

Press Win + R, type cmd, and press Enter.

**Type the following command to check if Python is installed and to see which version you installed:**

python --version
Or:

python -V

This should display the Python version number, such as Python 3.x.x, confirming that Python was installed correctly.

**To check if pip (the Python package manager) is also installed, run:**


pip --version
If you see the version number of pip, then Python and pip are both installed properly.

# **Step 4: (Optional) Install Additional Libraries with pip**

Once Python is installed, you can use the pip tool to install additional libraries. For example:


pip install numpy  # Install numpy
pip install pandas  # Install pandas
pip install requests  # Install requests library

# **Troubleshooting**

If the command python doesn't work or the version doesn't appear in Command Prompt, make sure:

You added Python to the PATH (this happens automatically if you checked the box during installation).
Restart Command Prompt or your computer after installation to refresh the environment variables.
