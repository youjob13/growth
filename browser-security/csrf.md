## CSRF

Cross-Site Request Forgery - это когда враждебный код пытается выполнить действия от имени авторизованного пользователя

## Методы защиты от CSRF

1. Не реализовывать state-changing операции в приложении через безопасные методы (GET, HEAD, OPTIONS, TRACE)
1. CSRF токены
2. Sec-Fetch заголовки (или фолбек сравнение source origin & target origin)
3. SameSite (Cookie attribute) - защищает от CSRF атак, ограничивая отправку cookie в зависимотси от того, откуда пришёл запрос. Помогает решить отправлять ли cookie с кросс-сайтовыми запросами (кроме CSRF методов подверженых риску e.g. POST, они запрещены)
   a) Lax - cookie отправляется при переходе по ссылке (навигации верхнего уровня) с другого сайта. Но не отправляется при фоновых запросах (fetch, XHR, загрузка изображений, iframe).
   b) Strict - cookie никогда не отправляется с запросами, инициированными с другого сайта, во всех cross-site browsing context (tab, window, popup, web application, frame or iframe). Даже если пользователь кликает по обычной ссылке.
   c) None

### Ограничения SameSite
- Lax блокирует только небезопасные методы (POST, PUT, DELETE etc.)
- SameSite ограничен регистрируемым доменом. Cookie добавленые на `app.example.com` с любым значением SameSite будут рассмотрены как "same-site", когда реквест выполняется из `anything.example.com` (multi-tenant SaaS on a shared parent domain)
- Top-level navigation and window-opening tricks - злоумышленник, имеющий возможность выполнять top-level навигацию или открыть новое окно (включая, window.open, prerendering hints или crafted link) может сгенерировать реквест, который браузер расценит как SameSite=Strict

   
