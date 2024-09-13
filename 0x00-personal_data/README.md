# Personal Data Management README

## Overview
This project focuses on managing personal data while maintaining security and privacy. It involves implementing functionality for filtering sensitive data in logs, encrypting passwords, and establishing secure connections to a database. The primary goal is to handle Personally Identifiable Information (PII) in compliance with best security practices.

## Learning Objectives
By completing this project, you will learn how to:
- Identify and handle Personally Identifiable Information (PII).
- Filter and obfuscate sensitive fields in log messages using regular expressions.
- Securely encrypt passwords and verify password validity.
- Connect to a MySQL database using environment variables for credentials.

## Requirements
- All files must be compatible with Ubuntu 18.04 LTS and Python 3.7.
- Ensure Python code adheres to the `pycodestyle` style guide.
- All Python files must be executable and end with a new line.
- Include appropriate documentation for modules, classes, and functions.
- Ensure type annotations are used for all functions.

## Tasks Breakdown

### 0. Regex-ing
Create a function `filter_datum` that obfuscates specific fields in a log message using regular expressions. The function should take the following parameters:
- `fields`: List of field names to obfuscate.
- `redaction`: String used to replace sensitive data.
- `message`: Log message string.
- `separator`: Separator character in the log message.

### 1. Log Formatter
Implement a class `RedactingFormatter` that inherits from `logging.Formatter`. The class should filter specific PII fields using the `filter_datum` function. The filtered fields are defined in the class constructor.

### 2. Create Logger
Implement a function `get_logger()` that returns a logger named `user_data`. The logger should:
- Use the `RedactingFormatter`.
- Log up to the `INFO` level.
- Include a `StreamHandler` that formats logs using the `RedactingFormatter`.

### 3. Connect to Secure Database
Create a function `get_db()` that connects to a MySQL database using environment variables for credentials:
- `PERSONAL_DATA_DB_USERNAME`, `PERSONAL_DATA_DB_PASSWORD`, `PERSONAL_DATA_DB_HOST`, and `PERSONAL_DATA_DB_NAME`.

### 4. Read and Filter Data
Implement a `main()` function that fetches data from a MySQL table called `users` and logs the data with sensitive fields obfuscated using the logger.

### 5. Encrypting Passwords
Create a function `hash_password()` that encrypts a password using bcrypt. The function should return the hashed password as a byte string.

### 6. Check Valid Password
Implement a function `is_valid()` that verifies if a provided password matches its encrypted version using bcrypt.

## Usage
1. Ensure all required dependencies are installed:
   ```bash
   pip install bcrypt mysql-connector-python
   ```
2. Set up your environment variables for the database credentials:
   ```bash
   export PERSONAL_DATA_DB_USERNAME=root
   export PERSONAL_DATA_DB_PASSWORD=password
   export PERSONAL_DATA_DB_HOST=localhost
   export PERSONAL_DATA_DB_NAME=my_db
   ```
3. Run your Python scripts:
   ```bash
   ./main.py
   ```

## Repository Structure
```bash
alx-backend-user-data/
├── 0x00-personal_data/
│   ├── filtered_logger.py
│   ├── encrypt_password.py
│   └── main.py
└── README.md
```

## References
- PII, Non-PII, and Personal Data
- bcrypt Documentation]
- MySQL Connector Documentation
