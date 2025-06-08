
# 📚 Panduan Belajar NestJS dari Dasar sampai Mahir

NestJS adalah framework backend modern berbasis Node.js dan TypeScript. Dibangun dengan pola arsitektur modular dan berbasis decorator, NestJS memudahkan pembuatan aplikasi skala besar dan enterprise-ready.

---

## 🧱 1. Pengenalan NestJS

### Tujuan
- Memahami apa itu NestJS
- Mengetahui alasan menggunakan NestJS

### Materi
- Apa itu NestJS?
- Filosofi dan arsitektur (terinspirasi Angular)
- Dibangun di atas Express atau Fastify
- Kapan sebaiknya menggunakan NestJS?
- Perbandingan: NestJS vs Express vs Koa

---

## ⚙️ 2. Instalasi & Setup Proyek

### Langkah-langkah
1. Install Nest CLI
   ```bash
   npm install -g @nestjs/cli
   ```

2. Buat project baru
   ```bash
   nest new nama-proyek
   ```

3. Struktur folder default:
   ```
   src/
     app.controller.ts
     app.service.ts
     app.module.ts
     main.ts
   ```

---

## 📦 3. Konsep Dasar NestJS

### Materi
- **Modules**: Container untuk fitur
- **Controllers**: Menangani HTTP request
- **Services (Providers)**: Menyimpan logika bisnis
- **Dependency Injection**: Injeksi service ke controller
- Overview Pipes, Guards, Interceptors

---

## 📡 4. Routing & HTTP Methods

### Materi
- Routing: GET, POST, PUT, DELETE
- Route parameters: `@Param()`
- Query parameters: `@Query()`
- Body data: `@Body()`
- Validasi input:
  ```bash
  npm install class-validator class-transformer
  ```

- Contoh DTO:
  ```ts
  import { IsString } from 'class-validator';

  export class CreateUserDto {
    @IsString()
    name: string;
  }
  ```

---

## 🗃️ 5. CRUD dengan Database

### Pilihan ORM:
- **TypeORM** (PostgreSQL, MySQL)
  ```bash
  npm install --save @nestjs/typeorm typeorm pg
  ```
- **Prisma** (lebih modern dan efisien)
  ```bash
  npm install prisma @prisma/client
  npx prisma init
  ```

### Materi
- Koneksi database
- Entity & schema
- CRUD:
  - Create: insert data
  - Read: fetch list/detail
  - Update: update data
  - Delete: hapus data

---

## 🔐 6. Autentikasi & Otorisasi

### Materi
- Instalasi JWT
  ```bash
  npm install @nestjs/jwt passport-jwt @nestjs/passport passport
  ```
- Guards: `@UseGuards()`
- Strategi auth (local vs jwt)
- Role-based Access Control

---

## 📄 7. Validasi & Error Handling

### Materi
- DTO & Validasi dengan Pipe
- Global ValidationPipe
  ```ts
  app.useGlobalPipes(new ValidationPipe());
  ```

- Exception Filter Custom
- HTTP Exceptions

---

## 🧩 8. Middleware & Interceptors

### Materi
- Middleware: Logging, Request Timing
- Interceptors: Modify response, Logging, Caching
- Custom Interceptors:
  ```ts
  @Injectable()
  export class LoggingInterceptor implements NestInterceptor {
    intercept(context: ExecutionContext, next: CallHandler): Observable<any> {
      console.log('Before...');
      return next.handle().pipe(tap(() => console.log('After...')));
    }
  }
  ```

---

## 🔄 9. Modul Global & Dynamic

### Materi
- Modul global: `@Global()`
- Dynamic Module Pattern:
  - Digunakan untuk konfigurasi fleksibel (ex: module auth, database, dll.)

---

## 🛰️ 10. Microservices dengan NestJS

### Materi
- Protocol: TCP, Redis, NATS, Kafka, RabbitMQ
- ClientProxy dan @MessagePattern()
- Event-based communication
- Contoh kasus:
  - Notifikasi terpisah
  - Layanan antrian email

---

## 📡 11. WebSocket (Real-Time)

### Materi
- Gunakan `@WebSocketGateway()`
- Gateway dan namespace
- Emit dan listen message
- Contoh: Real-time chat app

---

## 📦 12. Deployment

### Materi
- Build:
  ```bash
  npm run build
  ```

- Jalankan dengan PM2:
  ```bash
  pm2 start dist/main.js
  ```

- Dockerize:
  Contoh `Dockerfile`:
  ```Dockerfile
  FROM node:18-alpine
  WORKDIR /app
  COPY . .
  RUN npm install
  RUN npm run build
  CMD ["node", "dist/main"]
  ```

- Deployment ke VPS / Railway / Render / Vercel

---

## 🧪 13. Testing

### Materi
- Unit Test dengan Jest
- `@nestjs/testing` untuk mock service
- E2E Testing
- Contoh Unit Test:
  ```ts
  describe('AppService', () => {
    it('should return Hello World', () => {
      expect(service.getHello()).toBe('Hello World!');
    });
  });
  ```

---

## 📚 Rekomendasi Sumber Belajar

- 📘 [Dokumentasi Resmi NestJS](https://docs.nestjs.com)
- 🎥 [Traversy Media - NestJS Crash Course (YouTube)](https://www.youtube.com/watch?v=wqhNoDE6pb4)
- 🧪 [StackBlitz NestJS Playground](https://stackblitz.com/github/nestjs/typescript-starter)
- 📘 [Awesome NestJS Repo](https://github.com/nestjs/awesome-nestjs)

---

## 🎯 Tips Belajar Efektif

- Mulai dari konsep dasar (modul, controller, service)
- Latihan CRUD + Auth secara bertahap
- Dokumentasikan setiap kesalahan & solusinya
- Gunakan Git untuk versioning
- Bangun mini project: todo app, blog, API produk, dsb.

---

## ✅ Next Step (Opsional)

- Buat RESTful API lengkap
- Integrasi Frontend (React/Vue)
- Implementasi CI/CD
- Belajar GraphQL (NestJS mendukung!)
- Migrasi ke Microservices
- Kolaborasi dengan tim

---

_Selamat belajar dan ngoding dengan NestJS!_ 🔥
