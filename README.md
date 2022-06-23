# Nestjs API


## How to run on local machine
### Requirement:
Version: Nodejs version 14
Mysql v8
Redis

### Run API application
1. Create a `.env` file
   - Make `.env` file by copy from `.env.example`.
2. Edit env config
   - Edit file `.env` about information about database, redis connections
   - You can run database and redis by docker-compose.dev.yaml: `docker-compose -f docker-compose.dev.yaml`
3. Create a `ormconfig.json` file
  - Make `ormconfig.json` file by copy from `ormconfig.example.json`.
  - Edit file `ormconfig.json` to change the connection to your database.
3. Install dependencies:
```
npm i
```
4. Run Database migration:

- Run ```npm run typeorm:generate Init``` to generate migration file.
- Run ```npm run typeorm:run``` to import the structure of DB.
- After that, import the data about some tables need to be import first like Country, Category,... in the folder data/mysql.

5. Run:

```
npm run start:dev
```
## Production

```sh
npm run build
node dist/app
# OR
npm start
```

## Folders

```js
+-- bin // Custom tasks
+-- dist // Source build
+-- public // Static Files
+-- src
|   +-- config // Environment Configuration
|   +-- entity // TypeORM Entities generated by `typeorm-model-generator` module
|   +-- common // Global Nest Module
|   |   +-- filters // Nest Filters
|   |   +-- middleware // Nest Middleware
|   |   +-- providers // Nest Providers
|   |   +-- * // models, repositories, services...
|   +-- * // Other Nest Modules, non-global, same as common structure above
+-- typings // Modules and global type definitions

// Module structure
// Add folders according to module scale. If it's small, you don't need to add folders.
+-- src/greeter
|   +-- * // folders
|   +-- greeter.constant.ts
|   +-- greeter.controller.ts
|   +-- greeter.service.ts
|   +-- greeter.module.ts
|   +-- greeter.*.ts
|   +-- index.ts
```
### File Naming for Class

```ts
export class PascalCaseSuffix {} //= pascal-case.suffix.ts
// Except for suffix, PascalCase to hyphen-case
class FooBarNaming {} //= foo-bar.naming.ts
class FooController {} //= foo.controller.ts
class BarQueryDto {} //= bar-query.dto.ts
```

### Interface Naming

```ts
// https://stackoverflow.com/questions/541912
// https://stackoverflow.com/questions/2814805
interface User {}
interface CustomeUser extends User {}
interface ThirdCustomeUser extends CustomeUser {}
```

### Index Exporting

```diff
# It is recommended to place index.ts in each folder and export.
# Unless it's a special case, it is import from a folder instead of directly from a file.
- import { FooController } from './controllers/foo.controller';
- import { BarController } from './controllers/bar.controller';
+ import { FooController, BarController } from './controllers';
```

### Variables Naming

> refer to [Naming cheatsheet](https://github.com/kettanaito/naming-cheatsheet)