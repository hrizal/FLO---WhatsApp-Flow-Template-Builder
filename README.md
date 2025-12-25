# FLO - Modern WhatsApp Flow Designer

![FLO Preview](hero-preview.png)

**FLO** is a powerful, premium-grade visual builder for WhatsApp Flows. It allows developers and designers to create complex, multi-screen conversational interfaces using a drag-and-drop-like interface, real-time preview, and automated JSON generation based on the official WhatsApp Flow specification (v7.3+).

## ✨ Features

- **Visual Designer**: Add components like `TextInput`, `DatePicker`, `CheckboxGroup`, and `ImageCarousel` with a single click.
- **Real-Time Phone Preview**: See exactly how your flow looks and feels on a mobile device as you build it.
- **Multi-Screen Support**: Manage entire flows with multiple screens and automated/manual routing.
- **Smart Data Binding**: Easily bind UI components to dynamic data using `${data.variable}` tokens.
- **Advanced Screen Data Editor**: Scoped JSON editor for managing example/test data for your components.
- **Auto-Terminal Detection**: Automatically sets the `terminal` property for screens based on their actions (`data_exchange`, `complete`).
- **Markdown Support**: Built-in markdown editor for `TextBody` and `TextCaption` components.
- **Security First**: 
  - Sessions managed securely.
  - Restricted access to sensitive file types (.sql, .config, .backup).
  - Centralized logging and configuration outside the web root.

## 🛠️ Tech Stack

- **Backend**: Native PHP (8.x recommended).
- **Frontend**: Vanilla JavaScript (ES6+), Vanilla CSS3.
- **Database**: MySQL.
- **Icons**: Font Awesome 6.
- **Libraries**: `markdown-it` for rendering previews.

## 🚀 Installation & Setup

### 1. Prerequisites
- Apache/Nginx web server.
- PHP 8.0+ with MySQL extension.
- MySQL Database.

### 2. Database Configuration
Create a database and run the initialization script:
```bash
php setup_db.php
```

### 3. Folder Permissions
Ensure the following directories are writable by the web server (usually `www-data`):
- `/var/www/logs/` (for application logs)
- `/var/www/config/` (for configuration files)
- `/var/www/backup/` (for automated backups)

### 4. Configuration
Create your configuration file at `/var/www/config/flo.cfg`:
```ini
[database]
host = localhost
user = your_user
pass = your_password
name = flo_db

[api]
key = your_secure_api_key
```

### 5. Access
Navigate to the directory in your browser: `http://your-server/anyaman/flo/`.

## 📂 Project Structure

- `flo2.php`: The main application entry point.
- `js/`: 
  - `flo-core.js`: Globals, normalization, and utilities.
  - `flo-editor.js`: UI logic for the property panels and field rendering.
  - `flo-preview.js`: Real-time phone frame rendering.
  - `flo-json.js`: JSON construction, validation, and export logic.
  - `flo-main.js`: Event listeners and screen management.
- `includes/`: Core PHP logic (DB connects, sessions).
- `serve_js.php`: Helper for serving assets with cache-busting.

## 🔒 Security Recommendations

- **Folder Access**: Block direct access to `.md`, `.sql`, `.cfg`, and `.log` files in your web server configuration.
- **API Protection**: Always use the stored API key in headers when interacting with `save_json.php`.
- **Environment**: Keep the `/var/www/config/` and `/var/www/logs/` outside the public `anyaman` directory if possible, or use `.htaccess` to block access.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
Created with ❤️ by the Antigravity Team.
