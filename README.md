## Modern REST API for College Backend Management

[![License](https://img.shields.io/github/license/nishuR31/collegeBackend?style=flat)](LICENSE)
![Issues](https://img.shields.io/github/issues/nishuR31/collegeBackend?color=red&style=flat)
![Stars](https://img.shields.io/github/stars/nishuR31/collegeBackend?style=flat)
![Forks](https://img.shields.io/github/forks/nishuR31/collegeBackend?style=flat)
![Made With](https://img.shields.io/badge/Made%20with-Node.js-green?style=flat&logo=node.js&logoColor=white)

<br>

> 🔐 JWT Auth | 🎓 Role-based Access | 🧠 Forgot-Password Flow | 🧪 Mongoose + Express | 💻 Built by [@nishuR31](https://github.com/nishuR31)

<br>
<hr>
<br>

### 📁 Folder Structure

```
collegeBackend/
│
├── .env                  # Environment config
├── package.json
├── README.md
│
├── src/
│   ├── index.js          # App entry point
│   ├── app.js            # Express config
│   ├── routes/           # All routes (login, signup, logout, etc.)
│   ├── controllers/      # Business logic
│   ├── models/           # Mongoose schemas
│   ├── utils/            # OTP gen, token gen, etc.
│   ├── constants/        # HTTP codes, token secrets
│   ├── middlewares/      # JWT Auth, validators
│   └── config/           # MongoDB connection
```

<br>
<hr>
<br>

### ⚙️ Technologies Used

- **Node.js**
- **Express.js**
- **MongoDB + Mongoose**
- **JWT + Cookies**
- **bcrypt**
- **Email-based OTP**
- **Custom Middleware (auth, async, etc.)**

<br>
<hr>
<br>

### 👨‍💻 Features

- ✅ User Signup/Login (Admin, Faculty, Student)
- ✅ JWT Token + Refresh Token + Cookies
- ✅ Forgot Password → Email → OTP or Token → Change Password
- ✅ Role-based Access (`/admin`, `/faculty`, `/student`)
- ✅ Secure `res.cookie()` handling with `httpOnly`, `secure`, `sameSite`
- ✅ `timestamps: true` in schema for auditing
- ✅ All tokens hashed & verified using `bcrypt.compare()`

<br>
<hr>
<br>

### 🔐 Auth Flow (JWT + Cookies)

```
Login → Set Cookies (accessToken, refreshToken)
Logout → Clear Cookies
Refresh → Get new access token from refreshToken
```

```js
res.cookie("accessToken", token, {
  httpOnly: true,
  secure: true,
  sameSite: true,
});
```

<br>
<hr>
<br>

### 🔁 Forgot Password Flow

```js
POST /auth/:user/forgot-password     // Send email with OTP or token
POST /auth/:user/verify-token     // Verify OTP or token
POST /auth/:user/change-password     // Update password
```

```js
userSchema.pre("save", async function (next) {
  if (this.isModified("password")) {
    this.password = await bcrypt.hash(this.password, 10);
  }
  next();
});
```

<br>
<hr>
<br>

### 📦 API Sample

```js
POST / auth /  admin / signup;
POST / auth / faculty / signup;
POST / profile / username / logout;
```

```js
      edit: "POST /profile/:username/edit",
      deletion: "GET /profile/:username/deletion",
      forgotPassword: "POST /auth/forgot-password",
      verifyForgotToken: "POST /auth/verify-token",
      changePassword: "POST /auth/change-password",
      logout: "GET /profile/:username/logout",
      profile: "GET /profile/:username",
      signin: "POST /auth/:user/signin",
      signup: "POST /auth/:user/signup",
      tokenRotation: "GET /auth/:user/token-rotation",
      help: "GET /help"
```

<br>
<hr>
<br>

### 🌐 Sample `.env`

```env
PORT=port
MONGO_URI=mongodb uri
SECRET_ACC=token secret access
SECRET_REF=token secret refresh
MAIL_USER=sender email
MAIL_PASS=sender email app password //not email password
```

<br>
<hr>
<br>

### 🏗️ To Run Locally

```bash
git clone https://github.com/nishuR31/collegeBackend.git
cd collegeBackend
npm install
cp .env.example # helper env example
touch .env  # or make your .env file
npm run dev
```

<br>
<hr>
<br>

### 🛡️ Utils

- `asyncHandler`
- `ApiErrorHandler`
- `ApiHandler`
- `isEmptyArr`
- `comparePassword`
- `logger`
- `OTPGen`
- `required`
- `tokenGen`

<br>
<hr>
<br>

### 🧪 Sample Model Schema (User)

```js
const userSchema = new mongoose.Schema(
  {
    userName: { type: String, required: true, unique: true },
    email: { type: String, required: true, unique: true },
    password: { type: String, required: true },
    role: { type: String, enum: ["student", "faculty", "admin"] },
    otp: Number,
    token: String,
    refreshToken: String,
  },
  { timestamps: true }
);
```

<br>
<hr>
<br>

### 🤝 Contributing

PRs are welcome. If you like it, give it a ⭐ star!

<br>
<hr>
<br>

### 📫 Contact

[![nishuR31](https://img.shields.io/badge/Github-black?logo=github&logoColor=white&style=flat)](https://github.com/nishuR31)
[![nishanrajak01@gmail.com](https://img.shields.io/badge/Mail%20Me-black?logo=gmail&logoColor=white&style=flat)](mailto:nishanrajak01@gmail.com)
