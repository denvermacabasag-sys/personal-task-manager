# Personal Task Manager

Project Code: WST21-PM-2026-SF
Student Name: Comajig, Denver M.
Course & Year: BSIT-2 SECTION-5
Database Used: SQLite

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
- Blade templating engine
- Eloquent ORM
- MySQL database
- PHPUnit for testing

## Project Structure
- `app/Models/Task.php` — Eloquent model for tasks
- `app/Models/User.php` — Default User model (included for Laravel completeness)
- `app/Http/Controllers/TaskController.php` — handles all CRUD logic, status updates, and search/filter
- `app/Providers/AppServiceProvider.php` — application service provider
- `database/migrations/2014_10_12_000000_create_users_table.php` — default users table migration
- `database/migrations/2014_10_12_100000_create_password_reset_tokens_table.php` — password reset table
- `database/migrations/2019_08_19_000000_create_failed_jobs_table.php` — failed jobs table
- `database/migrations/2026_09_25_000000_create_tasks_table.php` — creates the `tasks` table
- `database/factories/TaskFactory.php` — model factory for testing tasks
- `database/factories/UserFactory.php` — model factory for testing users
- `database/seeders/DatabaseSeeder.php` — database seeder
- `routes/web.php` — defines all routes (resourceful + custom status route + root redirect)
- `routes/console.php` — Artisan console commands
- `resources/views/tasks/index.blade.php` — task list with search, filter, and statistics
- `resources/views/tasks/create.blade.php` — form to add a new task
- `resources/views/tasks/edit.blade.php` — form to edit an existing task
- `resources/views/layouts/app.blade.php` — shared layout and CSS styling
- `tests/Feature/TaskTest.php` — feature tests for CRUD operations
- `tests/Unit/ExampleTest.php` — basic unit test
- `phpunit.xml` — PHPUnit configuration

## Setup Instructions

1. Clone this repository:
   ```
   git clone <your-repo-url>
   cd task-manager
   ```

2. Install Composer dependencies:
   ```
   composer install
   ```

3. Copy the environment file and generate an app key:
   ```
   cp .env.example .env
   php artisan key:generate
   ```

4. Configure your database in `.env`:
   ```
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=task_manager
   DB_USERNAME=root
   DB_PASSWORD=
   ```

5. Create the database (e.g. via phpMyAdmin or the MySQL CLI):
   ```sql
   CREATE DATABASE task_manager;
   ```

6. Run the migrations to create the `tasks` table (and default Laravel tables):
   ```
   php artisan migrate
   ```

7. Serve the application:
   ```
   php artisan serve
   ```

8. Open the app in your browser:
   ```
   http://127.0.0.1:8000
   ```

### Running Tests
```
php artisan test
```

## How It Works
- **Routes** (`routes/web.php`) map URLs like `/tasks`, `/tasks/create`, `/tasks/{task}/edit` to controller methods. `Route::resource()` handles the standard CRUD actions (index, create, store, edit, update, destroy — `show` is excluded as it's not needed). A custom `PATCH` route toggles a task's status. A root redirect sends `/` to `/tasks`.
- **Controller** (`TaskController`) receives requests, validates input, and talks to the `Task` model to read/write the database. The `index` method supports optional `search` and `status` query parameters for filtering. It also computes statistics (total, pending, completed counts) and passes them to the view.
- **Model** (`Task`) is an Eloquent model mapped to the `tasks` table; `$fillable` allows mass assignment for `task_name`, `description`, `status`, and `due_date`. The `due_date` field is cast to a `date` for convenient formatting.
- **Database**: a `tasks` table with columns `id`, `task_name`, `description`, `status` (enum: Pending/Completed), `due_date`, and timestamps. Default Laravel migrations for users, password resets, and failed jobs are also included.
- **Blade Views**: 
  - `index.blade.php` lists all tasks in a table with statistics cards, a search bar, status filter buttons, overdue highlighting, and Edit/Delete/Mark-status actions for each task.
  - `create.blade.php` and `edit.blade.php` share the same form layout with validation error display for adding/updating a task.
  - `layouts/app.blade.php` provides a shared dark header, card-based layout, and consistent CSS styling.

## Architecture Flow
```
Route (web.php) → Controller (TaskController) → Model (Task) → Database (tasks table) → Blade View
```

## Screenshots
_(Add screenshots of your running app here once deployed.)_
