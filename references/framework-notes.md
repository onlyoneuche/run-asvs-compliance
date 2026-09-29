# Framework review cues

Use these cues to locate evidence. They are not substitutes for tracing the application path and reading the relevant ASVS control. If a stack is not listed, identify its own request lifecycle, security middleware, data access layer, and test conventions.

## Python / Django and Django REST Framework

- Trace URL patterns to views, DRF authentication and permission classes, object-level checks, serializers, and model writes.
- Check session or token settings, CSRF behavior for the actual authentication mode, cookie flags, and trusted origins in the deployed configuration.
- Check whether bulk `update`, `bulk_create`, raw SQL, or signals affect audit history and actor attribution. Inspect custom managers and database hooks.
- Look for Django/DRF tests, dependency lock files, container files, and CI configuration. A declared permission class is not proof that every object path uses it.

## JavaScript / TypeScript / Express and Node APIs

- Trace routers through middleware order, authentication, per-route authorization, validation, controller, and data access. Include error handlers and proxy configuration.
- Check session or JWT handling, cookie flags, CSRF for cookie-authenticated state changes, CORS, and trust-proxy behavior in the deployed setup.
- Inspect direct database queries and bulk mutations for authorization and audit coverage. Check package lock files, container images, and tests.
- Do not infer that importing security middleware means it runs on every route.

## Other stacks

- Identify the framework's authentication and authorization mechanisms, request validation, output encoding, session management, data access hooks, dependency lock format, and deployment settings from source and official framework documentation when needed.
- Follow changed and exposed routes end to end. State when framework behavior is uncertain or relies on production configuration that is unavailable.
