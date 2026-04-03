# Laravel API — Agent Instructions

**Copy this file to your Laravel project root and customize it.**

## Project Overview
- **Type:** Laravel API Backend (PHP)
- **Root:** [Your project path - e.g., D:\projects\edutalk-api]
- **Framework Version:** [Version - e.g., 11.x]
- **Port:** 8000 (`php artisan serve`)
- **Queue:** `php artisan queue:work --tries=3`

## Architecture

### Layer Structure
1. **Controllers** (`app/Http/Controllers/`)
   - HTTP handling only: validation, authorization, response
   - No business logic

2. **Services** (`app/Services/`)
   - All business logic
   - One service per domain
   - Type hints on all methods

3. **Repositories** (if applicable)
   - Database query abstraction
   - Named queries for filters

4. **DTOs** (`app/DTOs/`)
   - Type-safe data transfer
   - Complex request/response payloads

5. **Models** (`app/Models/`)
   - Eloquent models only
   - Relationships defined
   - Minimal logic

6. **Events** (`app/Events/`)
   - Side effects dispatched as events
   - Listeners handle notifications, logging

7. **Enums** (`app/Enums/`)
   - All status/type constants as enums
   - Example: `PaymentStatus`, `ExamType`

### Naming Conventions
- **Controllers:** `PascalCaseController`
- **Services:** `PascalCaseService`
- **DTOs:** `PascalCaseDTO`
- **Enums:** `PascalCase`
- **Methods:** `camelCase`, verb-first
- **Models:** `PascalCase` (singular)

## Key Domains

### Domain 1: [Name]
- **Models:** [related models]
- **Service:** [ServiceClass]
- **Key Operations:** [operation 1], [operation 2]

### Domain 2: [Name]
- **Models:** [related models]
- **Service:** [ServiceClass]
- **Key Operations:** [operation 1], [operation 2]

(Add your project domains)

## Database Setup

### Connection
- **Driver:** MySQL [or your DB]
- **Host:** [localhost or IP]
- **Database:** [your database name]
- **Migrations:** `database/migrations/`

### Migration Pattern
```php
Schema::create('table_name', function (Blueprint $table) {
    $table->id();
    $table->string('field')->nullable();
    $table->foreignId('user_id')->constrained()->onDelete('cascade');
    $table->timestamps();
});
```

### Relationships
- [List key relationships]
- Foreign keys properly configured
- Cascade settings documented

## Common Tasks

### Create New API Endpoint

1. **Create Controller method:**
```php
public function store(CreateResourceRequest $request)
{
    $resource = $this->service->create($request->validated());
    return response()->json(['data' => $resource], 201);
}
```

2. **Create FormRequest for validation:**
```php
class CreateResourceRequest extends FormRequest
{
    public function rules()
    {
        return [
            'field' => 'required|string|max:255',
        ];
    }
}
```

3. **Create Service method:**
```php
class ResourceService
{
    public function create(array $data): Resource
    {
        $resource = Resource::create($data);
        event(new ResourceCreated($resource));
        return $resource;
    }
}
```

4. **Add route:**
```php
Route::post('/resources', [ResourceController::class, 'store'])->middleware('auth:sanctum');
```

### Create Migration

1. **Generate migration:**
```bash
php artisan make:migration create_table_name
```

2. **Write up() and down():**
```php
public function up(): void
{
    Schema::create('table_name', function (Blueprint $table) {
        $table->id();
        $table->string('field')->nullable();
        $table->timestamps();
    });
}

public function down(): void
{
    Schema::dropIfExists('table_name');
}
```

3. **Test migration:**
```bash
php artisan migrate
php artisan migrate:rollback
php artisan migrate
```

### Create Console Command

1. **Generate command:**
```bash
php artisan make:command DoSomethingCommand
```

2. **Implement handle():**
```php
public function handle()
{
    try {
        $this->service->process();
        $this->info('Done!');
    } catch (Exception $e) {
        $this->error('Failed: ' . $e->getMessage());
        Log::error('Command failed', ['error' => $e]);
        return 1;
    }
}
```

### Write Tests

**Feature Test:**
```php
public function test_can_create_resource()
{
    $user = User::factory()->create();

    $response = $this->actingAs($user)->postJson('/api/resources', [
        'field' => 'value',
    ]);

    $response->assertStatus(201);
    $this->assertDatabaseHas('resources', ['field' => 'value']);
}
```

**Unit Test:**
```php
public function test_service_creates_resource()
{
    $service = new ResourceService();
    $resource = $service->create(['field' => 'value']);

    $this->assertInstanceOf(Resource::class, $resource);
    $this->assertEquals('value', $resource->field);
}
```

## Error Handling

### Custom Exceptions
```php
class ResourceNotFoundException extends Exception {}
class AuthorizationException extends Exception {}
```

### Exception Handler
```php
if ($exception instanceof ResourceNotFoundException) {
    return response()->json(['message' => 'Not found'], 404);
}
```

### Logging
```php
Log::info('Resource created', ['id' => $resource->id, 'user_id' => $user->id]);
Log::error('Payment failed', ['error' => $e->getMessage()]);
```

## Notifications

### Zalo ZNS (if applicable)
- Templates in `app/Abstracts/Zalo/`
- Dispatch events → Listeners send notifications
- Example: `event(new PaymentReminderEvent($payment))`

### Telegram (if applicable)
- Use TelegramService
- Dispatch events for messages
- Handle failures gracefully

## Run Commands

```bash
# Development Server
php artisan serve                    # Start dev server (port 8000)

# Database
php artisan migrate                  # Run migrations
php artisan migrate:rollback         # Rollback last batch
php artisan db:seed                  # Run seeders

# Queue
php artisan queue:work               # Start queue worker
php artisan queue:work --daemon      # Daemon mode

# Testing
php artisan test                     # Run all tests
php artisan test --filter=TestClass  # Run specific test
php artisan test tests/Feature/      # Run feature tests

# Cache
php artisan cache:clear              # Clear cache
php artisan config:cache             # Cache config

# Other
php artisan tinker                   # Interactive shell
php artisan artisan list             # List all commands
```

## Before Committing

Checklist:
- [ ] All methods have type hints
- [ ] Business logic in Services, not Controllers
- [ ] Tests exist and pass: `php artisan test`
- [ ] Migrations have up() and down()
- [ ] No hardcoded values or credentials
- [ ] Error handling in place
- [ ] Events dispatched for side effects
- [ ] Foreign keys have cascading configured
- [ ] No N+1 queries (use eager loading)
- [ ] Code follows naming conventions

## Code Review Criteria

✅ **Good:**
- Service layer with DI
- Type hints everywhere
- Tests with data factories
- Event-driven side effects
- Migrations with rollback

❌ **Issues:**
- Business logic in Controller
- Missing type hints
- No rollback in migration
- Direct service calls without events
- Hardcoded credentials

---

**Update this file as your architecture evolves!**
