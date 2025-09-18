# JWT-authentication-api

A robust authentication system built with Node.js, Express, and TypeScript that implements JWT (JSON Web Token) authentication with access and refresh tokens.

## Features

- 🔐 JWT-based authentication
- 🔄 Refresh token rotation
- 🍪 HTTP-only cookie security
- 📦 TypeScript support
- 🗄️ MongoDB integration
- 🔒 Password hashing with bcrypt
- ⚡ Express.js framework
- 🔑 Environment variable configuration

## Prerequisites

Before you begin, ensure you have installed:

- Node.js (v14 or higher)
- MongoDB (local installation or remote connection)
- npm or yarn package manager

## Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd <your-repo-name>
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory:
```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/auth-api
JWT_SECRET=your-super-secret-key-change-this
JWT_REFRESH_SECRET=your-super-secret-refresh-key-change-this
NODE_ENV=development
```

4. Start the development server:
```bash
npm run dev
```

## API Endpoints

### Authentication Routes

#### Login
```http
POST /auth/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "yourpassword"
}
```

**Response:**
- Access token in JSON response
- Refresh token in HTTP-only cookie
- User details

#### Refresh Token
```http
POST /auth/refresh
```
- Automatically uses refresh token from HTTP-only cookie
- Returns new access token
- Rotates refresh token

#### Logout
```http
POST /auth/logout
```
- Invalidates refresh token
- Clears refresh token cookie

## Security Features

- ⏰ Access tokens expire after 15 minutes
- 📅 Refresh tokens expire after 7 days
- 🔄 Single-use refresh tokens (rotation on each refresh)
- 🔒 Password hashing using bcrypt
- 🍪 HTTP-only cookies for refresh tokens
- 📝 Database tracking of refresh tokens

## Making Authenticated Requests

Include the access token in the Authorization header:
```http
Authorization: Bearer <your-access-token>
```

## Development

### Available Scripts

- `npm run dev` - Start development server with hot-reload
- `npm start` - Start production server
- `npm run build` - Build TypeScript code

### Project Structure

```
├── src/
│   ├── controllers/
│   │   └── auth.controller.ts
│   ├── models/
│   │   └── user.model.ts
│   └── index.ts
├── .env
├── package.json
├── tsconfig.json
└── README.md
```

## Production Considerations

Before deploying to production:

1. Change JWT secrets in `.env`
2. Implement rate limiting
3. Enable HTTPS
4. Add security headers
5. Set up proper error handling
6. Configure production MongoDB instance
7. Set NODE_ENV to 'production'

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Express.js team for the amazing framework
- MongoDB team for the robust database
- JWT community for secure token implementation

## Support

For support, email your-sabeel2311@gmail.com or open an issue in the repository.

---

Remember to star ⭐ this repository if you found it helpful!
