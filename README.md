# Personal Task Manager

Project Code: WST21-PM-2026-SF
Student Name: Comajig, Denver M.
Course & Year: BSIT-2 SECTION-5
Database Used: MySQL

## Features
- Add Task
- View Tasks
- Edit Task
- Delete Task
- Update Status (Pending / Completed)

### Additional Features
- **Search Tasks** — quickly find tasks by name or description
- **Status Filter** — filter tasks by All, Pending, or Completed status
- **Task Statistics** — cards showing total, pending, and completed task counts
- **Overdue Highlighting** — tasks with a past due date (still pending) are highlighted in red

## Tech Stack
- Laravel 11 (PHP framework)
- PHP 8.3
- Blade templating engine
- Eloquent ORM
- MySQL 8.4
- PHPUnit for testing
- Laragon for PHP and MySQL environment

## Setup Instructions
1. Clone this repository
git clone https://github.com/denvermacabasag-sys/personal-task-manager.git
cd personal-task-manager
2. Install Composer dependencies
composer install

If Composer is not added to PATH, use the Composer PHAR with PHP:

& "C:\laragon\bin\php\php-8.3.33-Win32-vs16-x64\php.exe" "C:\laragon\bin\composer.phar" install
3. Create the environment file
Copy-Item .env.example .env

Generate the Laravel application key:

php artisan key:generate
4. Configure the MySQL database

Update the .env file with the following database settings:

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=personal_task_manager
DB_USERNAME=root
DB_PASSWORD=
5. Start MySQL

If using Laragon, start the MySQL server.

If starting MySQL manually, use:

& "C:\laragon\bin\mysql\mysql-8.4.3-winx64\bin\mysqld.exe" --console

Keep the MySQL window open while using the application.

6. Create the database
& "C:\laragon\bin\mysql\mysql-8.4.3-winx64\bin\mysql.exe" -u root -e "CREATE DATABASE personal_task_manager;"
7. Run the migrations
php artisan migrate

This creates the required Laravel tables and the tasks table.

8. Start the Laravel application
php artisan serve
9. Open the application

Open the following address in your browser:

http://127.0.0.1:8000

For the task list:

http://127.0.0.1:8000/tasks
Running Tests
php artisan test

## Project Flow

The project demonstrates the Laravel development flow:

Routes → Controller → Model → Database → Blade

Routes — handles application URLs and requests
Controller — processes task operations
Model — communicates with the database using Eloquent ORM
Database — stores task information in MySQL
Blade — displays the user interface

## Screenshots
<img width="1917" height="957" alt="image" src="https://github.com/user-attachments/assets/ff09c759-4dd7-4e39-ba3c-6bc68960db53" />
<img width="1917" height="952" alt="image" src="https://github.com/user-attachments/assets/36b4b2ae-a652-434a-b88e-a19de385c766" />
<img width="1917" height="952" alt="image" src="https://github.com/user-attachments/assets/4c02c3f4-9bf8-422b-8085-b4146159f898" />




