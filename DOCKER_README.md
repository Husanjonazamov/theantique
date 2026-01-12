# TheAntique Laravel - Docker Setup

## Ishga Tushirish

### 1. Environment faylini nusxalash
```bash
cp .env.docker .env
```

### 2. Docker containerlarni ishga tushirish
```bash
docker-compose up -d
```

### 3. Composer dependencies o'rnatish
```bash
docker-compose exec app composer install
```

### 4. Application key generate qilish
```bash
docker-compose exec app php artisan key:generate
```

### 5. Storage link yaratish
```bash
docker-compose exec app php artisan storage:link
```

### 6. Database migratiyalarni ishga tushirish
```bash
docker-compose exec app php artisan migrate --seed
```

### 7. Cache tozalash
```bash
docker-compose exec app php artisan config:cache
docker-compose exec app php artisan route:cache
docker-compose exec app php artisan view:cache
```

## Foydalanish

- **Web**: http://localhost:8080
- **MySQL**: localhost:3307
  - Database: `6valley`
  - Username: `theantique_user`
  - Password: `theantique_password`
  - Root Password: `root`
- **Redis**: localhost:6380

## Foydali Commandlar

```bash
# Containerlarni ko'rish
docker-compose ps

# Loglarni ko'rish
docker-compose logs -f

# Container ichiga kirish
docker-compose exec app bash

# Containerlarni to'xtatish
docker-compose down

# Containerlar va volumelarni o'chirish
docker-compose down -v

# Qayta build qilish
docker-compose up -d --build
```

## Muammolarni hal qilish

### Permission xatoliklari
```bash
docker-compose exec app chown -R www-data:www-data /var/www/html
docker-compose exec app chmod -R 755 /var/www/html/storage
docker-compose exec app chmod -R 755 /var/www/html/bootstrap/cache
```

### Cache tozalash
```bash
docker-compose exec app php artisan cache:clear
docker-compose exec app php artisan config:clear
docker-compose exec app php artisan route:clear
docker-compose exec app php artisan view:clear
```

### Database qayta yaratish
```bash
docker-compose exec app php artisan migrate:fresh --seed
```
