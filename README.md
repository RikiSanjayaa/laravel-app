# 🚀 Laravel + Docker (Sail) Starter Project

This project is a Laravel application containerized using [Laravel Sail](https://laravel.com/docs/sail) — a light-weight Docker environment for Laravel. Designed to be easily cloned and run on any machine with Docker installed, no global PHP or Composer required.

---

## 🧱 Tech Stack

-   Laravel (PHP Framework)
-   Docker (via Laravel Sail)
-   MySQL (via Docker container)
-   Composer (used inside Docker)

---

## 🛠️ Getting Started

> NOTE: The Commands shown below are bash commands. to run it on Windows, use WSL CLI in the project directory

### 📦 Clone the Repository

```bash
git clone https://github.com/RikiSanjayaa/laravel-app.git
cd laravel-app
```

### 📝 Setup Environment

```bash
cp .env.example .env
```

Update `.env` as needed (e.g., database config).

---

### 🧰 Install Dependencies (Using Docker Composer)

```bash
docker run --rm -v $(pwd):/app -w /app laravelsail/php82-composer:latest composer install
```

> 💡 You do **not** need Composer or PHP installed locally.

---

### 🐳 Start Docker Containers

```bash
./vendor/bin/sail up -d
```

> TIP: use command `alias sail='bash vendor/bin/sail'` to shorten ./vendor/bin/sail to just `sail`

---

### 🔑 Generate App Key

```bash
./vendor/bin/sail artisan key:generate
```

---

### 🗃️ Run Migrations and Seeders (Optional)

```bash
./vendor/bin/sail artisan migrate --seed
```

---

## 🌐 Access Your App

Visit [http://localhost](http://localhost)

---

## 🧪 Useful Sail Commands

```bash
./vendor/bin/sail artisan migrate          # Run DB migrations
./vendor/bin/sail artisan db:seed          # Run DB seeders
./vendor/bin/sail artisan tinker           # Laravel REPL
./vendor/bin/sail npm install              # Install frontend deps (if using)
./vendor/bin/sail npm run dev              # Build frontend assets
```

---

## 🧼 Cleanup

To stop the containers:

```bash
./vendor/bin/sail down
```

To rebuild from scratch:

```bash
./vendor/bin/sail down -v
./vendor/bin/sail up -d
```

---

## 🧠 FAQ

### ❓ I don’t see the `vendor/` folder after cloning?

You need to run Composer via Docker:

```bash
docker run --rm -v $(pwd):/app -w /app laravelsail/php82-composer:latest composer install
```

---

### ❓ How can I view my MySQL database?

```bash
./vendor/bin/sail mysql -u sail -p
# Enter password: password (default)
```

Or connect with a GUI like DBeaver or TablePlus using:

-   Host: 127.0.0.1
-   Port: 3306
-   User: sail
-   Password: password
-   DB: laravel

---
