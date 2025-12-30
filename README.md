# 🏛️ Auction Management System - Backend

<div align="center">

![ASP.NET Core](https://img.shields.io/badge/ASP.NET%20Core-7.0-512BD4?style=for-the-badge&logo=dotnet)
![C#](https://img.shields.io/badge/C%23-11.0-239120?style=for-the-badge&logo=csharp)
![Entity Framework](https://img.shields.io/badge/EF%20Core-7.0-512BD4?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

**A robust RESTful API backend for Auction Management System built with ASP.NET Core Web API, featuring JWT authentication, Entity Framework Core, and comprehensive auction and bidding logic.**

[Features](#-features) • [Tech Stack](#️-tech-stack) • [Installation](#-installation) • [API Documentation](#-api-documentation) • [Deployment](#-deployment)

---

</div>

## 📋 Overview

The Auction Management Backend is a production-ready REST API that powers the complete auction platform. It provides secure endpoints for user authentication, auction management, real-time bidding, and administrative functions with role-based access control.

### 🎯 Why This Backend?

- **🔐 Secure by Design** - JWT authentication with role-based authorization
- **⚡ High Performance** - Optimized database queries with EF Core
- **📦 Well-Structured** - Clean architecture with separation of concerns
- **🔄 RESTful Design** - Standard HTTP methods and status codes
- **📊 Scalable** - Designed to handle concurrent bidding operations
- **🧪 Testable** - Dependency injection for easy unit testing

---

## 🚀 Features

### 👤 Authentication & Authorization
- ✅ **User Registration** - Secure account creation with validation
- ✅ **JWT Authentication** - Token-based authentication system
- ✅ **Password Hashing** - BCrypt password encryption
- ✅ **Role-Based Access Control** - Admin and User roles
- ✅ **Token Refresh** - Refresh expired tokens seamlessly
- ✅ **Account Verification** - Email verification for new users

### 🏷️ Auction Management
- ✅ **CRUD Operations** - Create, read, update, and delete auctions
- ✅ **Auction Status** - Active, Ended, Cancelled states
- ✅ **Time Management** - Start and end time validation
- ✅ **Search & Filter** - Find auctions by category, price, status
- ✅ **Image Upload** - Support for auction item images
- ✅ **Admin Controls** - Special privileges for auction management

### 💰 Bidding System
- ✅ **Place Bids** - Submit bids on active auctions
- ✅ **Bid Validation** - Ensure bids meet minimum increment
- ✅ **Bid History** - Track all bids for each auction
- ✅ **Current Winner** - Identify highest bidder
- ✅ **Auto-Close** - Automatically end auctions at deadline
- ✅ **Concurrent Handling** - Prevent race conditions in bidding

### 📊 Data Management
- ✅ **Entity Framework Core** - Robust ORM for database operations
- ✅ **Migrations** - Version-controlled database schema
- ✅ **Relationships** - Properly modeled data associations
- ✅ **Validation** - Data annotations and fluent validation
- ✅ **Soft Delete** - Preserve data integrity

### 🔍 Additional Features
- ✅ **Logging** - Comprehensive application logging
- ✅ **Error Handling** - Global exception handling middleware
- ✅ **API Versioning** - Support for multiple API versions
- ✅ **CORS** - Cross-origin resource sharing configuration
- ✅ **Swagger/OpenAPI** - Interactive API documentation
- ✅ **Health Checks** - Monitor application status

---

## 🛠️ Tech Stack

### Backend Framework
- **ASP.NET Core Web API** `7.0` - Modern web framework
- **C#** `11.0` - Primary programming language
- **.NET SDK** `7.0` - Runtime environment

### Data & ORM
- **Entity Framework Core** `7.0` - Object-relational mapper
- **SQL Server** - Primary database (configurable)
- **SQLite** - Development/testing database
- **PostgreSQL** - Alternative production database

### Authentication & Security
- **JWT (JSON Web Tokens)** - Token-based authentication
- **BCrypt.Net** - Password hashing
- **ASP.NET Core Identity** - User management (optional)

### Libraries & Tools
- **AutoMapper** - Object-to-object mapping
- **FluentValidation** - Input validation
- **Serilog** - Structured logging
- **Swashbuckle** - Swagger/OpenAPI documentation
- **Newtonsoft.Json** - JSON serialization

### Testing
- **xUnit** - Unit testing framework
- **Moq** - Mocking framework
- **FluentAssertions** - Assertion library

---

## 📥 Prerequisites

Before you begin, ensure you have the following installed:

| Requirement | Version | Download |
|-------------|---------|----------|
| .NET SDK | 7.0 or higher | [Download](https://dotnet.microsoft.com/download) |
| SQL Server | 2019 or higher | [Download](https://www.microsoft.com/sql-server) |
| Git | Latest | [Download](https://git-scm.com/) |
| Visual Studio / VS Code | Latest | [VS](https://visualstudio.microsoft.com/) / [VS Code](https://code.visualstudio.com/) |

### Optional Tools
- **SQL Server Management Studio (SSMS)** - Database management
- **Postman** - API testing
- **Docker** - Containerization

---

## 🧠 Installation and Setup

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/Bashi201/Auction-Management-Backend.git
cd Auction-Management-Backend
```

### 2️⃣ Configure Database Connection

Edit `appsettings.json` or `appsettings.Development.json`:

#### For SQL Server
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=AuctionDB;Trusted_Connection=True;TrustServerCertificate=True;"
  }
}
```

#### For PostgreSQL
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Host=localhost;Database=AuctionDB;Username=postgres;Password=yourpassword"
  }
}
```

#### For SQLite (Development)
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Data Source=auction.db"
  }
}
```

### 3️⃣ Configure JWT Settings

Add JWT configuration to `appsettings.json`:

```json
{
  "JwtSettings": {
    "SecretKey": "YourSuperSecretKeyThatIsAtLeast32CharactersLong!",
    "Issuer": "AuctionManagementAPI",
    "Audience": "AuctionManagementClient",
    "ExpirationMinutes": 60,
    "RefreshTokenExpirationDays": 7
  }
}
```

> ⚠️ **Security Warning:** Never commit your actual secret key to version control!

### 4️⃣ Restore Dependencies
```bash
dotnet restore
```

### 5️⃣ Apply Database Migrations
```bash
# Create initial migration (if not exists)
dotnet ef migrations add InitialCreate

# Update database
dotnet ef database update
```

### 6️⃣ Seed Database (Optional)
```bash
# Run seeder to add sample data
dotnet run --seed
```

### 7️⃣ Run the Application
```bash
# Development mode
dotnet run

# Or with hot reload
dotnet watch run
```

The API will be available at:
- **HTTPS:** `https://localhost:5001`
- **HTTP:** `http://localhost:5000`
- **Swagger:** `https://localhost:5001/swagger`

---

## 📁 Project Structure

```
Auction-Management-Backend/
├── Controllers/                    # API endpoints
│   ├── AuthController.cs          # Authentication endpoints
│   ├── AuctionsController.cs      # Auction management
│   ├── BidsController.cs          # Bidding operations
│   └── UsersController.cs         # User management
├── Models/                         # Entity models
│   ├── User.cs
│   ├── Auction.cs
│   ├── Bid.cs
│   └── Category.cs
├── DTOs/                           # Data Transfer Objects
│   ├── Auth/
│   │   ├── LoginDto.cs
│   │   ├── RegisterDto.cs
│   │   └── TokenDto.cs
│   ├── Auction/
│   │   ├── CreateAuctionDto.cs
│   │   ├── UpdateAuctionDto.cs
│   │   └── AuctionResponseDto.cs
│   └── Bid/
│       ├── PlaceBidDto.cs
│       └── BidResponseDto.cs
├── Data/                           # Database context
│   ├── ApplicationDbContext.cs
│   ├── DbInitializer.cs
│   └── Migrations/
├── Services/                       # Business logic
│   ├── Interfaces/
│   │   ├── IAuthService.cs
│   │   ├── IAuctionService.cs
│   │   └── IBidService.cs
│   └── Implementations/
│       ├── AuthService.cs
│       ├── AuctionService.cs
│       └── BidService.cs
├── Repositories/                   # Data access layer
│   ├── Interfaces/
│   │   ├── IUserRepository.cs
│   │   ├── IAuctionRepository.cs
│   │   └── IBidRepository.cs
│   └── Implementations/
│       ├── UserRepository.cs
│       ├── AuctionRepository.cs
│       └── BidRepository.cs
├── Middleware/                     # Custom middleware
│   ├── ErrorHandlingMiddleware.cs
│   └── JwtMiddleware.cs
├── Helpers/                        # Utility classes
│   ├── AutoMapperProfile.cs
│   ├── JwtHelper.cs
│   └── PasswordHelper.cs
├── Validators/                     # FluentValidation validators
│   ├── LoginDtoValidator.cs
│   ├── RegisterDtoValidator.cs
│   └── CreateAuctionDtoValidator.cs
├── appsettings.json               # Configuration
├── appsettings.Development.json   # Dev configuration
├── Program.cs                     # Application entry point
├── Startup.cs                     # Service configuration (if applicable)
├── AuctionApi.sln                 # Solution file
├── .gitignore
├── Dockerfile                     # Docker configuration
└── README.md
```

---

## 📘 API Documentation

### Base URL
```
https://localhost:5001/api
```

### Authentication
All protected endpoints require a JWT token in the Authorization header:
```
Authorization: Bearer <your_jwt_token>
```

---

## 🔐 Authentication Endpoints

### Register New User
```http
POST /api/auth/register
```

**Request Body:**
```json
{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@example.com",
  "password": "SecurePass123!",
  "confirmPassword": "SecurePass123!",
  "phoneNumber": "+1234567890"
}
```

**Response (201 Created):**
```json
{
  "success": true,
  "message": "Registration successful",
  "data": {
    "userId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "email": "john.doe@example.com",
    "firstName": "John",
    "lastName": "Doe"
  }
}
```

**cURL Example:**
```bash
curl -X POST https://localhost:5001/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com",
    "password": "SecurePass123!",
    "confirmPassword": "SecurePass123!"
  }'
```

---

### Login
```http
POST /api/auth/login
```

**Request Body:**
```json
{
  "email": "john.doe@example.com",
  "password": "SecurePass123!"
}
```

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "refreshToken": "7d5f8e9a-4b3c-2d1e-0f9g-8h7i6j5k4l3m",
    "expiresAt": "2024-12-31T23:59:59Z",
    "user": {
      "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "email": "john.doe@example.com",
      "firstName": "John",
      "lastName": "Doe",
      "role": "User"
    }
  }
}
```

**cURL Example:**
```bash
curl -X POST https://localhost:5001/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "john.doe@example.com",
    "password": "SecurePass123!"
  }'
```

---

### Refresh Token
```http
POST /api/auth/refresh
```

**Request Body:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "refreshToken": "7d5f8e9a-4b3c-2d1e-0f9g-8h7i6j5k4l3m"
}
```

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "refreshToken": "8e6g9f0b-5c4d-3e2f-1g0h-9i8j7k6l5m4n",
    "expiresAt": "2024-12-31T23:59:59Z"
  }
}
```

---

## 🏷️ Auction Endpoints

### Get All Auctions
```http
GET /api/auctions?page=1&pageSize=10&status=Active&category=Electronics
```

**Query Parameters:**
- `page` (int, optional): Page number (default: 1)
- `pageSize` (int, optional): Items per page (default: 10)
- `status` (string, optional): Filter by status (Active, Ended, Cancelled)
- `category` (string, optional): Filter by category
- `searchTerm` (string, optional): Search in title and description
- `minPrice` (decimal, optional): Minimum starting price
- `maxPrice` (decimal, optional): Maximum starting price
- `sortBy` (string, optional): Sort field (default: createdDate)
- `sortOrder` (string, optional): asc or desc (default: desc)

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "items": [
      {
        "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
        "title": "Vintage Camera",
        "description": "Rare vintage camera in excellent condition",
        "startingPrice": 500.00,
        "currentPrice": 750.00,
        "imageUrl": "https://example.com/images/camera.jpg",
        "startTime": "2024-12-01T10:00:00Z",
        "endTime": "2024-12-31T10:00:00Z",
        "status": "Active",
        "categoryName": "Electronics",
        "sellerName": "John Doe",
        "totalBids": 15,
        "highestBidder": "Jane Smith"
      }
    ],
    "currentPage": 1,
    "totalPages": 5,
    "totalItems": 50,
    "pageSize": 10
  }
}
```

**cURL Example:**
```bash
curl -X GET "https://localhost:5001/api/auctions?page=1&pageSize=10&status=Active" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

---

### Get Auction by ID
```http
GET /api/auctions/{id}
```

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "title": "Vintage Camera",
    "description": "Rare vintage camera in excellent condition. Includes original case and manual.",
    "startingPrice": 500.00,
    "currentPrice": 750.00,
    "imageUrl": "https://example.com/images/camera.jpg",
    "startTime": "2024-12-01T10:00:00Z",
    "endTime": "2024-12-31T10:00:00Z",
    "status": "Active",
    "categoryId": "cat-123",
    "categoryName": "Electronics",
    "sellerId": "user-456",
    "sellerName": "John Doe",
    "sellerEmail": "john.doe@example.com",
    "totalBids": 15,
    "highestBid": 750.00,
    "highestBidderId": "user-789",
    "highestBidderName": "Jane Smith",
    "createdAt": "2024-11-01T08:00:00Z",
    "updatedAt": "2024-12-15T14:30:00Z"
  }
}
```

---

### Create Auction (Admin/Seller Only)
```http
POST /api/auctions
```

**Headers:**
```
Authorization: Bearer YOUR_JWT_TOKEN
Content-Type: application/json
```

**Request Body:**
```json
{
  "title": "Vintage Camera",
  "description": "Rare vintage camera in excellent condition",
  "startingPrice": 500.00,
  "imageUrl": "https://example.com/images/camera.jpg",
  "startTime": "2024-12-01T10:00:00Z",
  "endTime": "2024-12-31T10:00:00Z",
  "categoryId": "cat-123"
}
```

**Response (201 Created):**
```json
{
  "success": true,
  "message": "Auction created successfully",
  "data": {
    "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "title": "Vintage Camera",
    "status": "Pending"
  }
}
```

**cURL Example:**
```bash
curl -X POST https://localhost:5001/api/auctions \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Vintage Camera",
    "description": "Rare vintage camera",
    "startingPrice": 500.00,
    "startTime": "2024-12-01T10:00:00Z",
    "endTime": "2024-12-31T10:00:00Z",
    "categoryId": "cat-123"
  }'
```

---

### Update Auction
```http
PUT /api/auctions/{id}
```

**Request Body:**
```json
{
  "title": "Updated Vintage Camera",
  "description": "Updated description",
  "startingPrice": 550.00,
  "endTime": "2025-01-15T10:00:00Z"
}
```

**Response (200 OK):**
```json
{
  "success": true,
  "message": "Auction updated successfully",
  "data": {
    "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "title": "Updated Vintage Camera",
    "updatedAt": "2024-12-30T15:45:00Z"
  }
}
```

---

### Delete Auction (Admin Only)
```http
DELETE /api/auctions/{id}
```

**Response (200 OK):**
```json
{
  "success": true,
  "message": "Auction deleted successfully"
}
```

---

## 💰 Bidding Endpoints

### Place Bid
```http
POST /api/bids
```

**Headers:**
```
Authorization: Bearer YOUR_JWT_TOKEN
Content-Type: application/json
```

**Request Body:**
```json
{
  "auctionId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "amount": 800.00
}
```

**Response (201 Created):**
```json
{
  "success": true,
  "message": "Bid placed successfully",
  "data": {
    "bidId": "bid-123",
    "auctionId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "amount": 800.00,
    "bidTime": "2024-12-30T16:00:00Z",
    "isHighestBid": true
  }
}
```

**cURL Example:**
```bash
curl -X POST https://localhost:5001/api/bids \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "auctionId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "amount": 800.00
  }'
```

---

### Get Auction Bid History
```http
GET /api/bids/auction/{auctionId}?page=1&pageSize=20
```

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "items": [
      {
        "id": "bid-123",
        "amount": 800.00,
        "bidTime": "2024-12-30T16:00:00Z",
        "bidderName": "Jane Smith",
        "isWinning": true
      },
      {
        "id": "bid-122",
        "amount": 750.00,
        "bidTime": "2024-12-30T15:45:00Z",
        "bidderName": "Bob Johnson",
        "isWinning": false
      }
    ],
    "currentPage": 1,
    "totalPages": 1,
    "totalItems": 15
  }
}
```

---

### Get User's Bid History
```http
GET /api/bids/my-bids?page=1&pageSize=10
```

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "items": [
      {
        "bidId": "bid-123",
        "auctionId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
        "auctionTitle": "Vintage Camera",
        "amount": 800.00,
        "bidTime": "2024-12-30T16:00:00Z",
        "status": "Winning",
        "currentHighestBid": 800.00
      }
    ],
    "currentPage": 1,
    "totalPages": 3,
    "totalItems": 25
  }
}
```

---

## 👥 User Management Endpoints

### Get User Profile
```http
GET /api/users/profile
```

**Response (200 OK):**
```json
{
  "success": true,
  "data": {
    "id": "user-456",
    "email": "john.doe@example.com",
    "firstName": "John",
    "lastName": "Doe",
    "phoneNumber": "+1234567890",
    "role": "User",
    "createdAt": "2024-01-15T10:00:00Z",
    "stats": {
      "totalBids": 45,
      "wonAuctions": 8,
      "activeAuctions": 3
    }
  }
}
```

---

### Update Profile
```http
PUT /api/users/profile
```

**Request Body:**
```json
{
  "firstName": "John",
  "lastName": "Doe",
  "phoneNumber": "+1234567890"
}
```

**Response (200 OK):**
```json
{
  "success": true,
  "message": "Profile updated successfully",
  "data": {
    "id": "user-456",
    "firstName": "John",
    "lastName": "Doe",
    "updatedAt": "2024-12-30T17:00:00Z"
  }
}
```

---

### Change Password
```http
PUT /api/users/change-password
```

**Request Body:**
```json
{
  "currentPassword": "OldPass123!",
  "newPassword": "NewSecurePass456!",
  "confirmNewPassword": "NewSecurePass456!"
}
```

**Response (200 OK):**
```json
{
  "success": true,
  "message": "Password changed successfully"
}
```

---

## 📊 Status Codes

| Code | Description |
|------|-------------|
| 200 | OK - Request succeeded |
| 201 | Created - Resource created successfully |
| 204 | No Content - Request succeeded, no content returned |
| 400 | Bad Request - Invalid input |
| 401 | Unauthorized - Authentication required |
| 403 | Forbidden - Insufficient permissions |
| 404 | Not Found - Resource not found |
| 409 | Conflict - Resource conflict (e.g., bid too low) |
| 422 | Unprocessable Entity - Validation errors |
| 500 | Internal Server Error - Server-side error |

---

## 🔒 Security Best Practices

### JWT Configuration
- Use strong secret keys (minimum 32 characters)
- Set appropriate token expiration times
- Implement refresh token rotation
- Store tokens securely on the client side

### Password Security
- Minimum 8 characters required
- Must include uppercase, lowercase, number, and special character
- Passwords are hashed using BCrypt with salt
- Implement rate limiting on login attempts

### API Security
- HTTPS enforced in production
- CORS properly configured
- Input validation on all endpoints
- SQL injection prevention through parameterized queries
- XSS protection enabled

### Environment Variables
Never commit sensitive data. Use environment variables:
```bash
# .env file (not committed)
JWT_SECRET=YourSuperSecretKey
DB_CONNECTION=YourDatabaseConnectionString
SMTP_PASSWORD=YourEmailPassword
```

---

## 🧪 Testing

### Run Unit Tests
```bash
dotnet test
```

### Run with Coverage
```bash
dotnet test /p:CollectCoverage=true /p:CoverageReportFormat=opencover
```

### Test with Postman
1. Import the Postman collection (if provided)
2. Set environment variables (base URL, token)
3. Run the collection

---

## 📦 Deployment

### Deploy to Azure App Service

#### 1. Publish the Application
```bash
dotnet publish -c Release -o ./publish
```

#### 2. Create Azure Resources
```bash
# Login to Azure
az login

# Create resource group
az group create --name AuctionAPIRG --location eastus

# Create App Service plan
az appservice plan create --name AuctionAPIPlan --resource-group AuctionAPIRG --sku B1

# Create web app
az webapp create --name auction-api-app --resource-group AuctionAPIRG --plan AuctionAPIPlan
```

#### 3. Configure Connection String
```bash
az webapp config connection-string set \
  --name auction-api-app \
  --resource-group AuctionAPIRG \
  --settings DefaultConnection="YOUR_CONNECTION_STRING" \
  --connection-string-type SQLAzure
```

#### 4. Deploy
```bash
az webapp deployment source config-zip \
  --resource-group AuctionAPIRG \
  --name auction-api-app \
  --src ./publish.zip
```

---

### Deploy with Docker

#### 1. Build Docker Image
```bash
docker build -t auction-api:latest .
```

#### 2. Run Container
```bash
docker run -d -p 8080:80 \
  -e ConnectionStrings__DefaultConnection="YOUR_CONNECTION_STRING" \
  -e JwtSettings__SecretKey="YOUR_JWT_SECRET" \
  --name auction-api \
  auction-api:latest
```

#### 3. Push to Docker Hub
```bash
docker tag auction-api:latest yourusername/auction-api:latest
docker push yourusername/auction-api:latest
```

---

### Deploy to AWS Elastic Beanstalk

```bash
# Install EB CLI
pip install awsebcli

# Initialize EB
eb init -p "64bit Amazon Linux 2 v2.x.x running .NET Core" auction-api

# Create environment and deploy
eb create auction-api-env
eb deploy
```

---

### Deploy to Heroku

```bash
# Login to Heroku
heroku login

# Create app
heroku create auction-api-app

# Add buildpack
heroku buildpacks:set https://github.com/jincod/dotnetcore-buildpack

# Deploy
git push heroku main

# Set environment variables
heroku config:set JWT_SECRET=YourSecretKey
heroku config:set ConnectionStrings__DefaultConnection="YOUR_CONNECTION"
```

---

## 🐳 Docker Setup

### Dockerfile
```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["AuctionApi.csproj", "./"]
RUN dotnet restore "AuctionApi.csproj"
COPY . .
RUN dotnet build "AuctionApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "AuctionApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "AuctionApi.dll"]
```

### docker-compose.yml
```yaml
version: '3.8'

services:
  api:
    build: .
    ports:
      - "8080:80"
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ConnectionStrings__DefaultConnection=Server=db;Database=AuctionDB;User=sa;Password=YourPassword123!;
    depends_on:
      - db
    networks:
      - auction-network

  db:
    image: mcr.microsoft.com/mssql/server:2019-latest
    environment:
      - ACCEPT_EULA=Y
      - SA_PASSWORD=YourPassword123!
    ports:
      - "1433:1433"
    volumes:
      - sqldata:/var/opt/mssql
    networks:
      - auction-network

volumes:
  sqldata:

networks:
  auction-network:
    driver: bridge
```

### Run with Docker Compose
```bash
docker-compose up -d
```

---

## 🗺️ Roadmap

- [ ] 📧 Email notifications for bid updates
- [ ] 🔔 Real-time WebSocket notifications
- [ ] 💳 Payment gateway integration (Stripe/PayPal)
- [ ] 📱 Push notifications
- [ ] 🌐 Multi-language support
- [ ] 📊 Advanced analytics and reporting
- [ ] 🤖 Auto-bidding system
- [ ] 📸 Image upload and management
- [ ] 🔍 Elasticsearch integration for advanced search
- [ ] 📈 Rate limiting and throttling
- [ ] 🔐 Two-factor authentication (2FA)
- [ ] 📄 Export data to PDF/Excel

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

### How to Contribute

1. **Fork** the repository
2. **Clone** your fork
   ```bash
   git clone https://github.com/your-username/Auction-Management-Backend.git
   ```
3. **Create** a feature branch
   ```bash
   git checkout -b feature/amazing-feature
   ```
4. **Make** your changes
5. **Run tests**
   ```bash
   dotnet test
   ```
6. **Commit** your changes
   ```bash
   git commit -m "Add: Amazing new feature"
   ```
7. **Push** to your fork
   ```bash
   git push origin feature/amazing-feature
   ```
8. **Open** a Pull Request

### Coding Standards
- Follow C# coding conventions
- Write XML documentation for public APIs
- Include unit tests for new features
- Update API documentation
- Keep commits atomic and well-described

---

## 🐛 Known Issues & Troubleshooting

### Issue: Migration Errors
```bash
# Reset database
dotnet ef database drop
dotnet ef database update
```

### Issue: JWT Token Not Working
- Ensure secret key is at least 32 characters
- Check token expiration time
- Verify Authorization header format: `Bearer {token}`

### Issue: CORS Errors
Update `Program.cs`:
```csharp
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowAll", builder =>
        builder.AllowAnyOrigin()
               .AllowAnyMethod()
               .AllowAnyHeader());
});
```

---

## 📄 License

This project is licensed under the **MIT License**.

```
MIT License

Copyright (c) 2024 Bashi201

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

## 👨‍💻 Author

**Bashi**

- 🌐 GitHub: [@Bashi201](https://github.com/Bashi201)
- 📧 Email:  bashithawanasinghe111@gmail.com

---

## 🙏 Acknowledgments

- **Microsoft** - For ASP.NET Core and Entity Framework
- **JWT.io** - For JSON Web Token implementation
- **Swagger** - For API documentation
- **Community Contributors** - Thank you for your support!

---

## 📈 Project Stats

![GitHub stars](https://img.shields.io/github/stars/Bashi201/Auction-Management-Backend?style=social)
![GitHub forks](https://img.shields.io/github/forks/Bashi201/Auction-Management-Backend?style=social)
![GitHub issues](https://img.shields.io/github/issues/Bashi201/Auction-Management-Backend)
![GitHub license](https://img.shields.io/github/license/Bashi201/Auction-Management-Backend)

---

<div align="center">

**Built with 💙 using ASP.NET Core by Bashi**

⭐ **If you find this project useful, please give it a star!** ⭐

[⬆ Back to Top](#️-auction-management-backend)

</div>
