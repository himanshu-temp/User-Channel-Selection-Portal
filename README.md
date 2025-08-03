# User Channel Selection Portal

This is a simple, modern web application designed for user authentication and managing a list of favorite channels. It allows users to register, log in, select channels from a pre-defined list, and save their preferences. The application features a clean, responsive design using Tailwind CSS and includes a dark/light mode toggle for enhanced user experience.

---

## ✨ Features

* **User Registration & Login**: Secure user authentication with password hashing.
* **Persistent Sessions**: Users remain logged in until they choose to log out.
* **Dynamic Channel Selection**: Fetches and displays a list of channels from a JSON file, allowing users to select their favorites.
* **Admin Panel**: A separate, password-protected admin area to:
    * Manage and delete user accounts.
    * View and delete saved channel preference files.
    * Copy shareable links and view the content of saved JSON files.
* **Modern UI**: Built with **Tailwind CSS** for a clean, responsive, and mobile-friendly interface.
* **Dark/Light Mode**: A user-friendly toggle to switch between dark and light themes, with preferences saved in local storage. The toggle button dynamically displays **emojis (☀️ and 🌙)** to indicate the current theme.

## 📁 Project Structure
```
├── admin.php         # Admin panel for managing users and saved data

├── index.php         # Main user interface for selecting favorite channels
├── login.php         # User login page
├── logout.php        # Script to destroy user sessions
├── register.php      # User registration page
├── save-channels.php # Backend endpoint to save user channel selections
├── data/             # Stores user credentials (users.json)
│   └── users.json
└── saved/
    └── username.json # Directory where individual user channel selections are stored as JSON files
```
## 🚀 Getting Started

Follow these steps to set up and run the project on your local machine.

### Prerequisites

* A web server with PHP installed (e.g., Apache, Nginx with PHP-FPM).
* PHP 7.4 or higher.

### Installation

1.  **Clone the repository:**

    ```bash
    git clone [repository-url]
    cd [repository-name]
    ```

2.  **Ensure directory permissions:**
    The `data/` and `saved/` directories must be writable by your web server. You might need to adjust their permissions:

    ```bash
    chmod -R 755 data/ saved/
    ```

3.  **Configure Admin Credentials (Optional but Recommended):**
    Open `admin.php` and locate the `$ADMIN_USERNAME` and `$ADMIN_PASSWORD` variables at the top. **It's highly recommended to change these default values for security reasons.**

    ```php
    $ADMIN_USERNAME = "admin"; // Change this
    $ADMIN_PASSWORD = "admin"; // Change this
    ```

4.  **Channel Data Source:**
    The application fetches channel data from a remote JSON file. The current URL used is:
    `https://raw.githubusercontent.com/himanshu-temp/temp/main/temp.json`

    If you wish to use a local JSON file for channels, you would need to modify the `CHANNELS_URL` constant in `index.php` to point to your local file path.

---

## 💡 Usage

1.  **Access the Application:**
    Open your web browser and navigate to the base URL where you've hosted the project (e.g., `http://localhost/your-project-folder/`). You will be automatically redirected to the `login.php` page.

2.  **Register a New Account:**
    * Click the **"Register"** link on the login page.
    * Fill in your desired username and password to create a new user account. Your credentials will be securely stored in `data/users.json`.

3.  **Select Favorite Channels:**
    * After successful registration or login, you will be taken to `index.php`.
    * Click on any channel card to select or deselect it. Selected cards will be highlighted.
    * Click the **"Save Selected Channels"** button at the bottom to save your preferences. These will be stored in a unique JSON file within the `saved/` directory, named after your user ID.

4.  **Logout:**
    * Click the **"Logout"** button in the header to end your session.

5.  **Admin Panel Access:**
    * To access the admin panel, navigate directly to `admin.php` in your browser (e.g., `http://localhost/your-project-folder/admin.php`).
    * Log in using the admin credentials configured in the setup steps.
    * From the admin dashboard, you can view and delete registered users, and inspect or delete the saved channel preference files.
