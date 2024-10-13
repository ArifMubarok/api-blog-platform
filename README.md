<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

-   [Simple, fast routing engine](https://laravel.com/docs/routing).
-   [Powerful dependency injection container](https://laravel.com/docs/container).
-   Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
-   Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
-   Database agnostic [schema migrations](https://laravel.com/docs/migrations).
-   [Robust background job processing](https://laravel.com/docs/queues).
-   [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

You may also try the [Laravel Bootcamp](https://bootcamp.laravel.com), where you will be guided through building a modern Laravel application from scratch.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains thousands of video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the [Laravel Partners program](https://partners.laravel.com).

### Premium Partners

-   **[Vehikl](https://vehikl.com/)**
-   **[Tighten Co.](https://tighten.co)**
-   **[WebReinvent](https://webreinvent.com/)**
-   **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
-   **[64 Robots](https://64robots.com)**
-   **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
-   **[Cyber-Duck](https://cyber-duck.co.uk)**
-   **[DevSquad](https://devsquad.com/hire-laravel-developers)**
-   **[Jump24](https://jump24.co.uk)**
-   **[Redberry](https://redberry.international/laravel/)**
-   **[Active Logic](https://activelogic.com)**
-   **[byte5](https://byte5.de)**
-   **[OP.GG](https://op.gg)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

install postgresql
ubah env menggunakan postgresql
Need install php versi 8.2 +, install laravel installer, install composer
mengaktifkan extension pdo_pgsql
cmd composer install

# API Documentation 📝

**Base Endpoint : `/api`**

## Auth Endpoint

> [!NOTE]
> Before using auth endpoint especially for login, your SPA's "login" page should first make a request to the `/sanctum/csrf-cookie` endpoint to initialize CSRF protection for the application:.
>
> ```axios.get('/sanctum/csrf-cookie').then(response => {
>    // Login...
> });
> ```
>
> During this request, Laravel will set an `XSRF-TOKEN` cookie containing the current CSRF token. This token should then be passed in an `X-XSRF-TOKEN` header on subsequent requests, which some HTTP client libraries like Axios and the Angular HttpClient will do automatically for you. If your JavaScript HTTP library does not set the value for you, you will need to manually set the `X-XSRF-TOKEN` header to match the value of the `XSRF-TOKEN` cookie that is set by this route.

| Method | Endpoint    | Params Required | Need Login | Body                                                                                                                        | Description               |
| ------ | ----------- | --------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| POST   | `/login`    | No params       | No         | `{"email": string\|required, "password": string\|required}`                                                                 | Login existing user       |
| POST   | `/register` | No params       | No         | `{"email": string\|required, "name": string\|required, "password": string\|required, "confirm_password": string\|required}` | Registration user         |
| POST   | `/logout`   | No params       | Yes        |                                                                                                                             | Logout authenticated user |

## Post Endpoint

**Endpoint : [base](#api-documentation-) + /post**

| Method | Endpoint   | Params Required | Need Login | Body                                                    | Description                                       |
| ------ | ---------- | --------------- | ---------- | ------------------------------------------------------- | ------------------------------------------------- |
| GET    | `/get-all` | No params       | No         | -                                                       | Get all posts                                     |
| GET    | `/`        | No params       | Yes        | -                                                       | Get all posts belonging to the authenticated user |
| GET    | `/{id}`    | Yes             | No         | -                                                       | Get detail one post                               |
| POST   | `/`        | No params       | Yes        | `{"title": string\|required, "body": string\|required}` | Create a new post for authenticated user          |
| PATCH  | `/{id}`    | Yes             | Yes        | `{"title": string\|optional, "body": string\|optional}` | Update a existing post for authenticated user     |
| DELETE | `/{id}`    | Yes             | Yes        | -                                                       | Delete a existing post for authenticated user     |

## Comment Endpoint

**Endpoint : [base](#api-documentation-) + /comment**

| Method | Endpoint       | Params Required | Need Login | Body                         | Description                                                     |
| ------ | -------------- | --------------- | ---------- | ---------------------------- | --------------------------------------------------------------- |
| GET    | `/user`        | No params       | Yes        | -                            | Get all comments that user have                                 |
| GET    | `/{postId}`    | Yes             | No         | -                            | Get all comments on detail post                                 |
| POST   | `/{postId}`    | Yes             | Yes        | `{"body": string\|required}` | Create a new comment on detail post for authenticated user      |
| PATCH  | `/{commentId}` | Yes             | Yes        | `{"body": string\|optional}` | Update a existing comment on detail post for authenticated user |
| DELETE | `/{commentId}` | Yes             | Yes        | -                            | Delete a existing comment on detail post for authenticated user |
