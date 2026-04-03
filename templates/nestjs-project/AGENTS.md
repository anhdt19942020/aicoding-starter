# NestJS API — Agent Instructions

**Copy this file to your NestJS project root and customize it.**

## Project Overview
- **Type:** NestJS API Backend (TypeScript)
- **Root:** [Your project path - e.g., D:\projects\citime-api]
- **Framework Version:** [Version - e.g., 10.x]
- **Port:** 3000 (`npm run start:dev`)
- **Database:** TypeORM + [PostgreSQL/MySQL/MongoDB]
- **Docker:** `docker-compose up -d`

## Architecture

### Module Structure
Each feature is a NestJS module with:
```
src/modules/{feature}/
├── {feature}.module.ts          # Module definition
├── {feature}.controller.ts      # HTTP routes
├── {feature}.service.ts         # Business logic
├── entities/
│   └── {feature}.entity.ts      # TypeORM entity
├── dtos/
│   ├── create-{feature}.dto.ts  # Request DTO
│   └── {feature}.response.dto.ts # Response DTO
├── {feature}.repository.ts      # Database queries
└── {feature}.module.spec.ts     # Module tests
```

### Decorators & Guards
- **Module:** `@Module({ controllers, providers, imports })`
- **Controller:** `@Controller('route')` + HTTP methods
- **Service:** `@Injectable()`
- **Guards:** `@UseGuards(AuthGuard)` on routes
- **DTOs:** Validation with `class-validator` decorators

### Naming Conventions
- **Modules:** `{feature}.module.ts`
- **Controllers:** `{feature}.controller.ts` with `@Controller('feature')`
- **Services:** `{feature}.service.ts` with `@Injectable()`
- **DTOs:** `create-{feature}.dto.ts`, `{feature}.response.dto.ts`
- **Entities:** `{feature}.entity.ts`
- **Methods:** `camelCase`, verb-first

## Key Domains

### Domain 1: [Name]
- **Module:** [FeatureModule]
- **Entity:** [FeatureEntity]
- **Key Operations:** [operation 1], [operation 2]

### Domain 2: [Name]
- **Module:** [FeatureModule]
- **Entity:** [FeatureEntity]
- **Key Operations:** [operation 1], [operation 2]

(Add your project domains)

## Database Setup

### TypeORM Configuration
- **Driver:** [PostgreSQL/MySQL/MongoDB]
- **Host:** [localhost or IP]
- **Database:** [your database name]
- **Entities:** Auto-loaded from `src/**/*.entity.ts`
- **Migrations:** `src/database/migrations/`

### Entity Pattern
```typescript
@Entity('table_name')
export class FeatureEntity {
  @PrimaryGeneratedColumn('uuid')
  id: string;

  @Column({ length: 255 })
  field: string;

  @ManyToOne(() => UserEntity, user => user.features)
  user: UserEntity;

  @CreateDateColumn()
  createdAt: Date;

  @UpdateDateColumn()
  updatedAt: Date;
}
```

### Relationships
- One-to-Many: `@OneToMany(() => Child, child => child.parent)`
- Many-to-One: `@ManyToOne(() => Parent, parent => parent.children)`
- Many-to-Many: `@ManyToMany(() => Other)`

## Common Tasks

### Create New API Endpoint

1. **Generate module (if needed):**
```bash
nest generate module modules/feature
nest generate controller modules/feature
nest generate service modules/feature
```

2. **Create DTO with validation:**
```typescript
import { IsString, IsEmail, IsNotEmpty } from 'class-validator';

export class CreateFeatureDto {
  @IsString()
  @IsNotEmpty()
  name: string;

  @IsEmail()
  email: string;
}
```

3. **Create Controller:**
```typescript
@Controller('features')
export class FeatureController {
  constructor(private featureService: FeatureService) {}

  @Post()
  @UseGuards(AuthGuard())
  create(@Body() createFeatureDto: CreateFeatureDto, @Request() req) {
    return this.featureService.create(createFeatureDto, req.user);
  }

  @Get(':id')
  @UseGuards(AuthGuard())
  findOne(@Param('id') id: string) {
    return this.featureService.findOne(id);
  }
}
```

4. **Create Service:**
```typescript
@Injectable()
export class FeatureService {
  constructor(private featureRepository: FeatureRepository) {}

  create(createFeatureDto: CreateFeatureDto, user: UserEntity) {
    const feature = this.featureRepository.create(createFeatureDto);
    feature.user = user;
    return this.featureRepository.save(feature);
  }

  findOne(id: string) {
    return this.featureRepository.findOne(id);
  }
}
```

5. **Add to Module:**
```typescript
@Module({
  imports: [TypeOrmModule.forFeature([FeatureEntity])],
  controllers: [FeatureController],
  providers: [FeatureService, FeatureRepository],
  exports: [FeatureService],
})
export class FeatureModule {}
```

### Create Database Migration

1. **Create entity changes in entity file**

2. **Generate migration:**
```bash
npm run typeorm migration:generate -- src/database/migrations/AddFieldToTable
```

3. **Review generated migration:**
```typescript
export class AddFieldToTable implements MigrationInterface {
  async up(queryRunner: QueryRunner): Promise<void> {
    await queryRunner.addColumn(
      'table_name',
      new TableColumn({
        name: 'field',
        type: 'varchar',
        isNullable: true,
      })
    );
  }

  async down(queryRunner: QueryRunner): Promise<void> {
    await queryRunner.dropColumn('table_name', 'field');
  }
}
```

4. **Test migration:**
```bash
npm run typeorm migration:run
npm run typeorm migration:revert
npm run typeorm migration:run
```

### Write Tests

**Unit Test (Service):**
```typescript
describe('FeatureService', () => {
  let service: FeatureService;
  let repository: FeatureRepository;

  beforeEach(async () => {
    const module = await Test.createTestingModule({
      providers: [
        FeatureService,
        {
          provide: FeatureRepository,
          useValue: { create: jest.fn(), save: jest.fn() },
        },
      ],
    }).compile();

    service = module.get<FeatureService>(FeatureService);
    repository = module.get<FeatureRepository>(FeatureRepository);
  });

  it('should create a feature', async () => {
    const createFeatureDto = { name: 'Test' };
    const feature = { id: '1', ...createFeatureDto };

    jest.spyOn(repository, 'create').mockReturnValue(feature);
    jest.spyOn(repository, 'save').mockResolvedValue(feature);

    expect(await service.create(createFeatureDto, user)).toEqual(feature);
  });
});
```

**Integration Test (E2E):**
```typescript
describe('Feature E2E', () => {
  let app: INestApplication;

  beforeAll(async () => {
    const moduleFixture: TestingModule = await Test.createTestingModule({
      imports: [AppModule],
    }).compile();

    app = moduleFixture.createNestApplication();
    await app.init();
  });

  it('POST /features should create feature', () => {
    return request(app.getHttpServer())
      .post('/features')
      .set('Authorization', 'Bearer token')
      .send({ name: 'Test' })
      .expect(201)
      .expect((res) => {
        expect(res.body.data).toHaveProperty('id');
      });
  });
});
```

## Error Handling

### Custom Exceptions
```typescript
export class ResourceNotFoundException extends BadRequestException {
  constructor(resource: string) {
    super(`${resource} not found`);
  }
}
```

### Exception Filter
```typescript
@Catch()
export class AllExceptionsFilter implements ExceptionFilter {
  catch(exception: any, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const response = ctx.getResponse();

    response.status(exception.getStatus()).json({
      message: exception.message,
      errors: exception.getResponse()?.message,
      statusCode: exception.getStatus(),
    });
  }
}
```

### Logging
```typescript
export class LoggingInterceptor implements NestInterceptor {
  intercept(context: ExecutionContext, next: CallHandler) {
    const request = context.switchToHttp().getRequest();
    this.logger.log(`${request.method} ${request.url}`);
    return next.handle();
  }
}
```

## Events & Listeners (if applicable)

### Dispatch Event
```typescript
constructor(private eventEmitter: EventEmitter2) {}

create(createDto: CreateDto) {
  const feature = this.featureRepository.create(createDto);
  this.eventEmitter.emit('feature.created', feature);
  return feature;
}
```

### Listen to Event
```typescript
@OnEvent('feature.created')
handleFeatureCreated(payload: FeatureEntity) {
  // Send notification, log, etc.
}
```

## Run Commands

```bash
# Development
npm run start                   # Build and start
npm run start:dev              # Dev mode with hot reload
npm run start:debug            # Debug mode

# Testing
npm test                       # Run unit tests
npm run test:watch             # Watch mode
npm run test:cov               # Coverage report
npm run test:e2e               # E2E tests

# Database
npm run typeorm migration:generate -- src/database/migrations/Name
npm run typeorm migration:run   # Run pending migrations
npm run typeorm migration:revert # Revert last migration

# Build
npm run build                  # Build for production
npm run start:prod             # Start production build

# Database (Docker)
docker-compose up -d           # Start containers
docker-compose down            # Stop containers
docker-compose logs -f         # View logs
```

## Before Committing

Checklist:
- [ ] All parameters have type hints
- [ ] All return types specified
- [ ] DTOs have validation decorators
- [ ] Business logic in Services only
- [ ] Tests exist and pass: `npm test`
- [ ] No hardcoded values or credentials
- [ ] Error handling in place
- [ ] Guards applied to protected routes
- [ ] Migrations have up() and down()
- [ ] No N+1 queries (use eager loading)
- [ ] Code follows naming conventions

## Code Review Criteria

✅ **Good:**
- Module with DI setup
- Type-safe Entities and DTOs
- Validation decorators on DTOs
- Service layer with business logic
- Tests with mocked dependencies
- Migrations with rollback

❌ **Issues:**
- Business logic in Controller
- Missing type hints
- No DTOs or validation
- Direct database access in Controller
- Unmockable dependencies
- Incomplete migrations

---

**Update this file as your architecture evolves!**
