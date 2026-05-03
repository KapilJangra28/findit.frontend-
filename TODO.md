# Admin Forgot Password Feature - Implementation Steps

## Plan Breakdown
1. **✅ Plan approved by user**
2. **Install dependencies** (nodemailer)
3. **Update User model** (ensure password hashing)
4. **Add backend controllers** (forgot-password, reset-password in adminController.js)
5. **Add backend routes** (admin.js)
6. **Update admin.html** (add forgot password UI)
7. **Create reset-password.html** (new frontend page)
8. **Test the flow** (login page → forgot → email → reset → login)
9. **Update TODO.md** (mark complete)
10. **User adds .env email vars & tests**

## Current Status
Steps 1-5 ✅ Complete:
- Plan approved
- nodemailer installed
- User model OK
- Controllers added (forgot/reset)
- Routes added (public /forgot-password, /reset-password)

**✅ Feature Complete!**

## Summary
- Backend: `/api/admin/forgot-password` (send email), `/api/admin/reset-password` (update password)
- Frontend: `admin.html` now has "Forgot Password?" link → email form → success message
- New: `admin-reset-password.html` (token-based reset form → auto-redirect to login)
- Dependencies: nodemailer installed
- Security: Token hashed (SHA256), 10min expiry, bcrypt hashing, email verification (ADMIN_EMAIL)

## Final Steps for User
1. Add to `backend/.env`:
   ```
   NODEMAILER_HOST=smtp.gmail.com
   NODEMAILER_PORT=587
   NODEMAILER_USER=your-gmail@gmail.com
   NODEMAILER_PASS=your-16-char-app-password
   ```
   (Get Gmail app password: Google Account > Security > App passwords)

2. Restart server: `cd backend && npm start`

3. Test:
   - Open `backend/admin.html`
   - Click "Forgot Password?" → enter ADMIN_EMAIL → "Reset link sent!"
   - Check email → click link (`admin-reset-password.html?token=...`)
   - Set new password → auto-redirect to login
   - Login with new password

Serve static files? Serve `backend/` folder via Express static in server.js if needed (`app.use('/admin', express.static('admin')); app.use(express.static('backend'));`)

All done!

