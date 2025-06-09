+++
date = '2025-06-08T20:19:54-05:00'
draft = false
title = 'Databases'
featured_image = "/images/admin_page.png"
+++

This is the third improvement project that I have chosen to showcase as part of my Computer Scence Capstone Class.

The artifact that I have chosen for this category is my full-stack
development website utilizing the MEAN stack. This application is
derived from my CS-465 Full-Stack Development 1 class. I have chosen
this artifact because it provides me with a great framework to showcase
my ability to improve a full-stack application. I specifically planned
to implement Authorization security procedures for users which access
the Mongo Database in this application.

I completed a code review prior to implementing improvements to the project. The link to this code review is provided here:
https://youtu.be/ULIRyS-XVs4

This is a shared link to view my project files which contain the original and improved versions:
https://1drv.ms/f/c/cacfa31f2f94c006/EklswLSiti1Lr95UDVES3ScBN0wrbd4wiHL-lY0bzRqOKQ?e=UrFo5g

This is the Code Review Script that I used for my Analysis:

3.  **Category Three: Databases**

    1.  Provide a clear, complete description of existing code
        **functionality**.

        1.  What does the code do?

            - The artifact that I have chosen for this category is my
              full-stack development website utilizing the MEAN stack.
              This application is derived from my CS-465 Full-Stack
              Development 1 class. I have chosen this artifact because
              it provides me with a great framework to showcase my
              ability to improve a full-stack application. I
              specifically plan to implement Authorization security
              procedures for users which access the Mongo Database in
              this application. This application specifically provides
              users with a website that contains listings for available
              vacation trips that they could potentially go on. In this
              code review I will specifically focus on the code that
              consists of the Single Page Application accessed by
              administrators wishing to make changes to the website.
              This SPA provides administrators with the ability to see
              trip cards on a single page which dynamically adjusts
              based on screen size. Each trip card has buttons with
              which the admin can edit trip details or delete the trip.
              These changes then reflect on the client website. There is
              also an add trip button which allows administrators to add
              a trip. To view these buttons, administrators must click
              the log in button at the top right of the screen and then
              complete sign in with the correct sign in details.

        2.  Focus on the features and functions of the existing code.

            - Trip Cards

            - See Trip Details

            - Add Trips

            - Edit Trips

            - Delete Trips

            - User authentication

            - Operation buttons hidden when not sign in

    2.  **Analyze** existing code using relevant code review criteria to
        support clearly stated findings.

        1.  Use the checklist to review the code critically. This review
            might highlight weaknesses, such as not following secure
            coding best practices, having no error handling, code not
            being efficient, code that needs debugging, and so on. Not
            all the items on the checklist will be applicable, so review
            the ones that are applicable to your artifact.

> **Login.component.ts**

- Here's a structured code review of your **MEAN stack login
  component**, using the checklist you provided:

- **Structure**

- The code correctly implements the design of a login component using
  Angular.

- It follows TypeScript and Angular coding standards, but styleUrl
  should be corrected to styleUrls.

- The component structure is clean and modular, with necessary
  dependencies imported correctly.

- No unused procedures or unreachable code detected.

- The component does not contain repeated logic that could be moved into
  reusable services.

- Storage usage appears efficient, as credentials are handled within the
  component state.

- No magic numbers, but setTimeout introduces an arbitrary delay
  (3000ms). This value should be configurable rather than hardcoded.

- **Documentation**

- The code lacks inline comments, which would be helpful for
  maintainability.

- The purpose of setTimeout is unclear—comments explaining why this
  delay is used would be beneficial.

- Removing commented-out debugging (console.log) would improve
  cleanliness.

- **Variables**

- Variables are properly defined with meaningful names (credentials,
  newUser, formError).

- Type consistency is maintained.

- No redundant or unused variables detected.

- **Arithmetic Operations**

- No arithmetic operations are present, so floating-point comparison and
  rounding errors are not relevant.

- **Loops and Branches**

- The IF conditions in onLoginSubmit properly validate input fields.

- The most common failure condition (empty credentials) is tested first.

- The default navigation in router.navigateByUrl('#') is
  ineffective—consider redirecting to an appropriate login error page
  instead.

- In doLogin, the conditional
  if(this.authenticationService.isLoggedIn()) correctly directs the user
  but lacks a **clear failure handling mechanism**.

- **Defensive Programming**

- No input sanitization is visible. Validation checks prevent empty
  fields, but **no explicit protections** exist against malformed or
  malicious inputs.

- No error handling for authentication failures—if login fails, there’s
  no feedback or retry mechanism.

- The **setTimeout** retry pattern is unreliable—it should rely on
  authentication observables or asynchronous event tracking instead.

- formError is assigned a message but never displayed in the
  template—ensure it integrates with UI feedback mechanisms.

> **App\_api/Authentication.js**

- Here’s a structured code review of the **authentication controller**
  for your MEAN stack application using the CS 499 checklist:

- **Structure**

- The code correctly implements **user authentication** using Mongoose
  and Passport.js.

- The function naming (register, login) is intuitive and follows common
  authentication conventions.

- No excessive complexity, but register could benefit from better
  **error-handling mechanisms**.

- No unnecessary functions or unreachable code detected.

- The **use of symbolics** for message strings is appropriate, avoiding
  magic numbers.

- **Efficiency**: The user model is used correctly, though error
  handling could be improved for robustness.

- **Documentation**

- **Lack of comments**: While function purposes are evident, adding
  **inline documentation** explaining JWT generation and password
  handling would improve clarity.

- Comments should describe **why** specific error cases are handled a
  certain way, rather than just summarizing the function logic.

- **Variables**

- Variable names (user, q, token) are mostly clear, but q is **not
  descriptive**—renaming to something meaningful like savedUser would
  enhance readability.

- Proper type consistency is maintained.

- No redundant or unused variables detected.

- **Arithmetic Operations**

- No arithmetic operations are present, so floating-point comparison
  issues are **not relevant**.

- **Loops and Branches**

- **IF conditions** correctly validate input presence.

- The **login function’s error-checking** branches (if (user), if (err))
  are clear, but handling **user authentication failures** could be more
  detailed.

- The authentication response should **explicitly log failure reasons**
  for debugging.

- **Using passport.authenticate('local') properly**, but consider
  **returning structured error messages** when authentication fails.

- **Defensive Programming**

- **Missing error handling in register**:

- await user.save() should wrap in a try-catch block instead of checking
  if(!q). If an error occurs, err is undefined, which may lead to
  issues.

- **Login function does not sanitize inputs**—while Passport handles
  authentication, directly validating or sanitizing user input would
  strengthen security.

- **Generated JWT is returned in plaintext**—this is standard, but
  **consider including expiration times** for security enhancement.

- **Potential vulnerability**: No checks on **email validation** or
  **password strength** during registration. This leaves room for weak
  passwords.

- **Error handling in passport.authenticate is minimal**—consider
  handling cases where authentication fails due to incorrect credentials
  more explicitly.

> **App\_api/models/user.js**

- Here’s a **structured code review** of the **user model** in your MEAN
  stack application, based on the **CS 499 checklist**:

- **Structure**

- The **Mongoose schema** is well-defined, correctly modeling a user
  with essential fields (email, name, hash, salt).

- The **password hashing mechanism** follows security best practices
  using crypto.pbkdf2Sync with a **salt**.

- No unnecessary procedures or unreachable code detected.

- Storage efficiency is maintained—fields are appropriately stored.

- **No excessive complexity**, but certain methods (setPassword,
  validPassword) could be **refactored** for better modularization.

- No magic numbers—**constants for PBKDF2 iterations and key length**
  (1000, 64) could be defined as configurable values instead.

- **Documentation**

- The **JWT generation method includes a useful inline comment**, but
  overall, documentation is minimal.

- **Lack of comments** in setPassword and validPassword—adding
  explanations would improve maintainability.

- No misleading comments detected.

- **Variables**

- **Variable names are clear** (hash, salt, userSchema).

- Proper type consistency is maintained.

- The variable hash inside validPassword could be renamed to **a more
  descriptive name** (computedHash) for clarity.

- **Arithmetic Operations**

- No direct arithmetic operations are present, so concerns about
  floating-point equality, rounding errors, or zero divisors do not
  apply.

- **Loops and Branches**

- No loops or branching logic are present—the schema primarily defines
  methods for password security and authentication.

- **Defensive Programming**

- **Missing error handling** in setPassword—using a **try-catch block**
  would improve robustness.

- **No validation for email format**—consider adding an **email
  validation check** to ensure a properly formatted email address.

- **JWT generation relies on process.env.JWT\_SECRET**—this is good
  practice, but ensuring that it is **properly loaded and handled** at
  runtime is crucial.

- **Password hashing security**:

- **PBKDF2 key stretching iterations (1000) could be increased**—modern
  recommendations suggest **higher iteration counts** (e.g.,
  **10,000+**) for added security.

- The hashing algorithm **uses SHA-512**, which is strong, but consider
  **bcrypt** for better built-in protection against brute-force attacks.

> **App\_api/config/passport.js**

- Here's a structured **code review** of your **Passport.js
  configuration** using the **CS 499 Code Review Checklist**:

- **Structure**

- The implementation correctly follows **Passport.js best practices**
  for a **local authentication strategy**.

- No unused procedures or unreachable code detected.

- The LocalStrategy constructor **correctly specifies** that
  authentication should use the email field (usernameField: 'email').

- No excessive complexity—logic is clear and **concise**, but **error
  handling could be improved**.

- **Storage efficiency:** The query logic retrieves a **single user
  record**, which is appropriate for authentication.

- No **"magic numbers"**, but **symbolic error codes/messages** could be
  used instead of hardcoded strings.

- **Documentation**

- **Minimal comments**—adding brief explanations for **Passport.js
  workflow** and authentication behavior would improve maintainability.

- **Uncommented console log statement**—consider either removing or
  documenting its purpose.

- **Variables**

- Variable q is **not descriptive**—renaming it to userRecord or
  foundUser would improve readability.

- No unused or redundant variables detected.

- Proper type consistency is maintained.

- **Arithmetic Operations**

- No arithmetic operations present, so **floating-point concerns** are
  not relevant.

- **Loops and Branches**

- **IF conditions** correctly handle authentication logic, but
  passport.authenticate does **not include explicit error handling**.

- The authentication flow is structured logically:

- **Checks if the user exists (if (!q))**

- **Checks if the password is valid (if (!q.validPassword(password)))**

- **Returns the user if credentials are correct**

- **No default error catch**—consider adding **a catch block** to handle
  potential **database or unexpected failures**.

- **Most common cases tested first** (if (!q) runs before password
  validation), ensuring efficiency.

- **Defensive Programming**

- **Error handling is minimal**—if User.findOne fails due to database
  errors, it **does not return a structured response**.

- **No input sanitization**—since user credentials come from req.body,
  additional validation (e.g., **email format checking**) would enhance
  security.

- **Missing try-catch block**—await User.findOne({ email: username })
  could fail under certain conditions. Wrapping it in a try-catch
  ensures **robust error handling**.

- **Valid password check relies on an instance method**
  (q.validPassword(password))—this is correct, but consider logging
  failed authentication attempts for security monitoring.

> **App\_admin/src/app/services/authentication.service.ts**

- Here's a **structured code review** of the **authentication service**
  for the SPA frontend, using the CS 499 checklist:

- **Structure**

- The **authentication service** correctly implements essential
  authentication logic.

- The code adheres to **Angular service conventions** with proper
  dependency injection (@Inject(BROWSER\_STORAGE)).

- No excessive complexity—each method is well-contained and serves a
  clear purpose.

- Storage use is efficient; however, **no encryption or security
  measures are applied** to local storage, which is a security risk.

- No repeated code, but error-handling logic is minimal.

- No unnecessary procedures, though error messages should be structured
  for better debugging.

- **Documentation**

- **Minimal inline comments**—comments exist for token storage and
  logout behavior but could be expanded.

- **Missing explanation of security risks**—storing JWTs in local
  storage exposes the app to potential **XSS (Cross-Site Scripting)**
  attacks. This should be documented or mitigated.

- No misleading comments.

- **Variables**

- Variable naming is **clear and meaningful** (authResp, token, user).

- **Type consistency is maintained**, but let out: any; could be
  explicitly typed (let out: string | null;).

- No redundant or unused variables detected.

- **Arithmetic Operations**

- No arithmetic operations are present, though **token expiration check
  (payload.exp &gt; (Date.now() / 1000)) relies on time-based
  arithmetic**. This could fail in edge cases if client-side time
  settings are incorrect.

- **Loops and Branches**

- Conditional checks are correct, ensuring token retrieval and validity
  in isLoggedIn().

- **Missing default error handling in login/register methods**—failed
  authentication should provide structured error feedback instead of
  just logging the error (console.log('Error: ' + error)).

- No loop termination conditions required in this service.

- **Defensive Programming**

- **Storage Security Issue**:

- JWT **should not be stored in local storage** due to XSS risks. A more
  secure approach is **HTTP-only cookies**.

- **No error handling for token parsing**:

- If JSON.parse(atob(token.split('.')\[1\])) fails (due to an invalid or
  malformed JWT), it will cause runtime errors. Adding a **try-catch
  block** would improve robustness.

- **No sanitization of user input** before sending credentials via
  login() and register().

- **No validation for email format or password strength** before
  authentication attempts.

> **App\_admin/src/app/login/login.component.ts**

- Here's a **structured code review** of your **Angular login
  component**, using the **CS 499 Code Review Checklist**:

- **Structure**

- The component correctly implements **user authentication**, handling
  form submission and routing.

- It follows **Angular component conventions**, with necessary
  dependencies injected (Router, AuthenticationService).

- No excessive complexity detected, but **logic for login validation
  could be improved** for clarity.

- No unnecessary procedures, but router.navigateByUrl('#') is
  ineffective—it should redirect to a **specific error page** instead.

- **Storage efficiency is good**, but validation methods could be
  externalized into a utility function.

- No **magic numbers**, though the **3000ms delay in setTimeout should
  be configurable instead of hardcoded**.

- **Documentation**

- Minimal comments—**login flow lacks clear explanations**.

- **Commented-out console.log statements** should be removed or properly
  documented for debugging use.

- No misleading comments detected.

- **Variables**

- **Variable names are clear** (credentials, formError, newUser).

- **submitted variable is declared but never used**—should either be
  removed or utilized for tracking form submission state.

- No redundant variables detected.

- **Arithmetic Operations**

- No arithmetic operations present, but **time-based arithmetic
  (setTimeout) could be error-prone** if the user's system clock is
  inaccurate.

- **Loops and Branches**

- IF conditions correctly validate input presence in onLoginSubmit(),
  but **error messages should be displayed in the UI instead of just
  being assigned**.

- Login retry logic using setTimeout is **inefficient**—consider using
  **observables or event-driven authentication updates** instead.

- **No default failure handling in authentication logic**—if
  authentication fails, the response should provide structured feedback.

- **Defensive Programming**

- **No input sanitization** before submitting credentials—potential
  **security risk** for malformed input.

- **No error handling for authentication failures**—doLogin() does not
  catch unexpected errors or provide feedback beyond UI navigation.

- **router.navigate(\[''\]) should ensure that authenticated state is
  truly confirmed before redirecting**.

- **Potential timing issue with setTimeout**—relying on this method for
  authentication verification is unreliable.

1.  Target areas for improvement such as structure, logic, efficiency,
    functionality, security, testing, commenting, and documenting.

> **Login.component.ts**

- **Suggested Improvements**

- **Improve Documentation**—add meaningful comments explaining login
  flow and retry logic.

- **Handle Authentication Failures**—provide user feedback when login
  fails rather than relying on setTimeout.

- **Fix Navigation Handling**—replace router.navigateByUrl('#') with
  proper redirection after failed login.

- **Enhance Security**—sanitize user input and prevent potential
  injection risks.

- **Use Observables for Login Status**—replace setTimeout with an
  event-driven approach for login validation.

- Would you like help refactoring the authentication logic to improve
  reliability and error handling?

> **App\_api/Authentication.js**

- **Suggested Improvements**

- **Improve Error Handling**—wrap user.save() in a try-catch block to
  properly handle Mongoose errors.

- **Enhance Security**—validate and sanitize email and password inputs
  before processing.

- **Better Logging & Debugging**—provide detailed failure messages in
  the login function for improved debugging.

- **Refine JWT Generation**—consider adding expiration times and
  encoding best practices for token security.

- **Strengthen Password Handling**—ensure passwords meet complexity
  requirements before allowing registration.

- Would you like help implementing these improvements, or refining error
  handling further?

> **App\_api/models/user.js**

- **Suggested Improvements**

- **Enhance Documentation**—add comments explaining **password
  hashing**, **salting**, and **JWT generation** for clarity.

- **Improve Error Handling**—wrap password-setting logic in try-catch to
  handle unexpected failures.

- **Refine Naming Conventions**—rename hash in validPassword to
  something more descriptive (computedHash).

- **Increase PBKDF2 Iterations**—update iteration count **beyond 1000**
  for stronger protection against brute-force attempts.

- **Implement Email Validation**—use a **regex or built-in validation**
  to ensure email format integrity.

- **Consider Using bcrypt**—bcrypt offers **automatic salt handling**
  and is **better suited for password security**.

- Would you like guidance on implementing stronger authentication
  security practices?

> **App\_api/config/passport.js**

- **Suggested Improvements**

- **Improve Error Handling**—wrap User.findOne in a **try-catch** block
  and provide a structured error response.

- **Refine Variable Naming**—rename q to something more descriptive
  (userRecord, foundUser).

- **Enhance Documentation**—add comments to **clarify authentication
  flow and Passport.js behavior**.

- **Strengthen Security**—validate and sanitize email input to prevent
  malformed entries.

- **Handle Unexpected Errors**—include a **catch-all failure response**
  in passport.authenticate for **database query failures**.

- **Consider Logging Failed Logins**—track failed authentication
  attempts for potential **security monitoring**.

- Would you like me to help refactor the authentication logic to include
  better error handling and security practices?

> **App\_admin/src/app/services/authentication.service.ts**

- **Suggested Improvements**

- **Improve Token Storage Security**—use **HTTP-only cookies** instead
  of local storage for JWTs.

- **Implement Error Handling for Token Parsing**—wrap JWT parsing in a
  **try-catch** block to handle malformed tokens.

- **Strengthen Login Failure Handling**—instead of console logging
  errors, provide structured error responses in the UI.

- **Validate and Sanitize User Input**—ensure credentials are properly
  formatted before sending authentication requests.

- **Improve Documentation**—explain the risks of local storage and why
  authentication security matters.

- Would you like help implementing these improvements, particularly
  around **secure authentication practices**?

> **App\_admin/src/app/login/login.component.ts**

- **Suggested Improvements**

- **Improve Error Handling**—ensure login failures provide **structured
  feedback** rather than just assigning formError.

- **Remove Hardcoded Timeout**—replace setTimeout with **event-driven
  authentication checks**.

- **Enhance Documentation**—add inline comments explaining
  **authentication flow** and **login handling mechanisms**.

- **Validate and Sanitize User Input**—ensure credentials meet format
  and security standards before submitting authentication requests.

- **Fix Navigation Handling**—replace router.navigateByUrl('#') with
  proper redirection logic.

- Would you like assistance in **refactoring authentication logic for
  better reliability and security**?

1.  Explain practical **enhancements** aligned with analysis findings in
    a clear and organized manner.

    1.  Say what you plan to do in your enhancement. What specific
        skills will you demonstrate, and which of the five course
        outcomes will your enhancements support?

> I will introduce Authorization strategies in this application by
> enhancing the existing authentication framework present for the SPA
> (Single Page Application) as well as the client-side website. I will
> create user access privileges which determine whether certain CRUD
> operations are allowed. This will involve the creation of three user
> types: General User, Teller, and Admin. General users will have the
> ability to submit update requests which do not actually change any
> entries in the database itself, which they will not have access
> privileges for. The Teller will be able to edit trip details
> performing update operations to existing trips. The admin user will be
> the only user which has access privileges to perform all CRUD
> operations. The specific skills that I will demonstrate will be my
> ability to work within the MEAN stack and implement improvements and
> changes to existing code. I will also demonstrate my understanding of
> how to implement Authorization security processes to the MEAN stack.
> The specific course outcomes that this enhancement addresses are
> numbers one and five. This enhancement demonstrates strategies which
> foster a full-stack application that addresses the needs of the
> diverse audience of users present in a website dedicated to showing
> available vacations. This includes users on both the backend and
> frontend of development as well as the clients themselves. In addition
> to this, I am implementing a security practice which perfectly aligns
> with the security mindset outlined in outcome five. Authorization will
> represent a further layer of security following the defense in depth
> concept so that an exploit which allowed the creation of a user would
> not be sufficient to make changes to the database.
