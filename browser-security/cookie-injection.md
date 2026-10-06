## Cookie injection

## Способы защиты

1. Использование *cookies prefix*. Префикс это специальное начало имени cookie, которое говорит браузеру "эта cookie обладает расширенными гарантиями безопасности"
a) `__Host-`
```http
Set-Cookie: __Host-session=abc123; Path=/; Secure; HttpOnly; SameSite=Lax
```
