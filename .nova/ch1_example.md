# Chapter 1: Authentication

*This chapter handles user registration, login, and session management.*

---

## Section 1.1: AuthModels

*Database models for authentication.*

#### Paragraph: UserModel
RENDERS AS "database-model" NAMED "User".

FIELD: **id** is string. Required is true. Must be unique.
FIELD: **email** is string. Required is true. Must be unique.
FIELD: **name** is string. Required is true.
FIELD: **password** is string. Required is true.
FIELD: **role** is Role. Default is "member".
FIELD: **createdAt** is date. Automatically set to current time.

---

## Section 1.2: AuthService

*Business logic for authentication. This section is a class grouping related auth methods.*

FIELD: **jwtSecret** is string. *Loaded from environment config.*

#### Paragraph: registerUser
RENDERS AS "api-endpoint" AT "POST /api/auth/register".

!**email** must be a valid email.
!**password** must be at least 8 characters.
!**name** must not be empty.

**existingUser** is User found by email.
existingUser exists? Return error 400 "Email already registered".

**hashedPassword** is password | hash with bcrypt.
**newUser** is a new User.
Set newUser.email to email.
Set newUser.name to name.
Set newUser.password to hashedPassword.
Save newUser to database.

**token** is JWT signed with jwtSecret containing newUser.id.
Return 201 with token and newUser.

#### Paragraph: loginUser
RENDERS AS "api-endpoint" AT "POST /api/auth/login".

!**email** must be a valid email.
!**password** must not be empty.

**user** is User found by email.
user does not exist? Return error 401 "Invalid credentials".

**passwordMatch** is password | compare with user.password using bcrypt.
passwordMatch is false? Return error 401 "Invalid credentials".

**token** is JWT signed with jwtSecret containing user.id.
Return 200 with token and user.

#### Paragraph: getCurrentUser
RENDERS AS "api-endpoint" AT "GET /api/auth/me".

!Request must have valid authorization header.

**token** is authorization header | extract bearer token.

Try this.
  **decoded** is token | verify with jwtSecret.
  **user** is User found by decoded.id.
  user does not exist? Return error 404 "User not found".
  Return 200 with user.
If it fails?
  Return error 401 "Invalid or expired token".
End try.

---

## Section 1.3: AuthGuard

*Middleware that protects routes requiring authentication.*

#### Editor: requireAuth
*This is a middleware (Editor's Note) — it runs BEFORE any paragraph that CITES it.*

**token** is request authorization header | extract bearer token.
token is missing? Return error 401 "Authentication required".

Try this.
  **decoded** is token | verify with jwtSecret.
  **user** is User found by decoded.id.
  user does not exist? Return error 401 "User no longer exists".
  Attach user to request.
  Continue to next paragraph.
If it fails?
  Return error 401 "Invalid or expired token".
End try.

#### Editor: requireAdmin
*This Editor CITES requireAuth — it runs after requireAuth.*
CITES Editor: requireAuth from ch1_example.

request.user.role is not "admin"? Return error 403 "Admin access required".
Continue to next paragraph.

---

## Section 1.4: AuthUI

*User interface components for authentication.*

#### Paragraph: LoginForm
RENDERS AS "react-component" NAMED "LoginForm".

CALLS "useState" from "react".

NARRATOR REMEMBERS: **isLoading** is false.

*Layout: A centered card with email and password fields.*

Centered on page with surface background, rounded-lg, shadow-medium.

Inside the container add a column layout with spacing lg:
  - Heading: "Welcome Back" with text-primary, font-size-2xl, font-weight-bold.
  - Text input for **email** with placeholder "Enter your email".
  - Text input for **password** with placeholder "Enter your password". Type is password.
  - Button: "Sign In" with primary background, rounded-md, text-inverse.
    On hover? Darken to primary-hover with transition-fast.
    On click? Set isLoading to true. Call loginUser with email and password.

#### Proofread: LoginForm should render
*Test that LoginForm renders without errors.*
Render LoginForm.
Expect heading "Welcome Back" to be visible.
Expect email input to be present.
Expect password input to be present.
Expect "Sign In" button to be present.
