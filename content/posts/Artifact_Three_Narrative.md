+++
date = '2025-06-08T20:10:41-05:00'
draft = false
title = 'Artifact Three Narrative'
featured_image = "/images/avatar4.jpg"
+++

Artifact Three Narrative

**Travlr Authentication System Enhancement and Debugging**

**Artifact Overview**

The artifact that I have chosen for this category is my full-stack
development website utilizing the MEAN stack. This application is
derived from my CS-465 Full-Stack Development 1 class. I have chosen
this artifact because it provides me with a great framework to showcase
my ability to improve a full-stack application. I specifically planned
to implement Authorization security procedures for users which access
the Mongo Database in this application.

The artifact presented in this paper is a Travlr website system
developed using Angular for the frontend and Express.js for the backend.
This system now allows users to securely log in using JSON Web Tokens
(JWT) stored in cookies, ensuring authentication without exposing
sensitive credentials. The system was initially developed to provide a
seamless user authentication experience while maintaining security best
practices. Over time, improvements were made to refine the handling of
authentication tokens, enhance error reporting, and resolve technical
challenges related to frontend-backend communication.

**Justification for Inclusion**

This artifact is included in the portfolio because it demonstrates a
comprehensive approach to debugging and improving authentication
workflows. Secure authentication is a fundamental component of modern
web applications, and the enhancements applied to this system reflect
proficiency in implementing security principles, refining software
functionality, and addressing real-world technical challenges.
Specifically, the improvements highlight skills in debugging
cross-origin authentication failures, resolving API communication
errors, ensuring proper token storage, and providing user-friendly error
feedback.

By including this artifact, I am showcasing my ability to methodically
refine a system, troubleshoot errors in both frontend and backend
components, and implement best practices in web security and
authentication. The enhancements made throughout the process contribute
to a more robust, maintainable, and efficient authentication solution.

**Improvements Made to the Artifact**

One of the key improvements involved fixing JWT retrieval timing issues
in Angular’s HTTP interceptor. Previously, authentication headers were
inconsistently applied due to asynchronous retrieval of JWT tokens. This
was resolved by modifying the method of extracting JWT directly from
cookies, ensuring that authentication headers are set immediately.

const cookieString = document.cookie;

const cookies = cookieString.split("; ").reduce((acc, cookie) =&gt; {

const \[name, value\] = cookie.split("=");

acc\[name\] = decodeURIComponent(value);

return acc;

}, {} as Record&lt;string, string&gt;);

const token = cookies\["jwt"\];

if (token) {

const authReq = request.clone({

setHeaders: { Authorization: \`Bearer ${token}\` }

});

return next.handle(authReq);

}

Additionally, one of the significant technical issues encountered was
the incorrect port mapping between Angular and Express.js. Initially,
the frontend was making authentication requests to port 4200, whereas
the backend was running on port 3000. This caused repeated 404 errors
when attempting to log in. The solution involved explicitly setting the
API request to target the correct backend port.

this.http.post("http://localhost:3000/api/login", { email: user.email,
password: passwd }, { withCredentials: true });

To ensure proper cross-origin communication between Angular and
Express.js, modifications were made to the backend CORS configuration.
Without these updates, API requests from the frontend were rejected due
to security restrictions.

app.use('/api', (req, res, next) =&gt; {

res.header('Access-Control-Allow-Origin', 'http://localhost:4200');

res.header('Access-Control-Allow-Headers', 'Origin, X-Requested-With,
Content-Type, Accept, Authorization");

res.header('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE');

res.header('Access-Control-Allow-Credentials', 'true');

next();

});

Another crucial improvement was the enhancement of error handling in the
login workflow. Previously, login failures were only logged in the
console, providing no direct feedback to users. This was resolved by
correctly updating the formError property in the login component.

public formError: string = '';

onLoginSubmit(): void {

this.authenticationService.login(this.credentials.email,
this.credentials.password)

.subscribe({

next: (response: any) =&gt; {

alert("Welcome back! You are now logged in.");

this.authenticationService.saveToken(response.token);

this.router.navigate(\['/trips'\]);

},

error: (error: any) =&gt; {

this.ngZone.run(() =&gt; {

this.formError = "Invalid email or password. Please try again.";

});

}

});

}

This update ensured that error messages are displayed directly within
the login form, providing immediate feedback to users in case of
incorrect credentials.

**Meeting Course Outcomes**

The enhancements applied to this authentication system align with
several key computer science program outcomes. Firstly, the debugging
and iterative improvement of the login system illustrate the ability to
design and evaluate computing solutions that solve authentication
challenges using established software engineering principles. The
modifications also reflect proficiency in designing professional-quality
written communication, particularly in documenting issues and resolving
them systematically.

Additionally, the process reinforced a security mindset, ensuring that
authentication vulnerabilities were minimized and that proper practices
in token storage and cross-origin handling were followed. The final
refinements also demonstrate strategic collaborative problem-solving as
multiple aspects of authentication were addressed collectively,
balancing security considerations with usability.

**Reflection on the Enhancement Process**

Enhancing this authentication system required methodical problem-solving
and debugging across multiple layers of the application. One of the most
valuable lessons learned throughout this process was the importance of
correctly handling asynchronous operations, particularly in
authentication workflows. The issue of missing authentication headers
was a direct result of delayed JWT retrieval, and understanding this
timing issue was crucial in implementing a proper solution.

Additionally, resolving API request failures due to incorrect port
configurations reinforced the need to carefully manage frontend-backend
communication. The process of fixing these issues required structured
debugging approaches, including verifying route registration, checking
request headers, and ensuring proper data flow between client and
server.

Another challenge encountered was ensuring that user error feedback was
correctly displayed within the UI. While login errors were being logged
in the console, the user interface remained unchanged, creating a
disconnect in user experience. The final solution involved leveraging
Angular’s change detection mechanism to ensure UI updates occurred as
expected.

Overall, the refinement of this authentication system strengthened my
ability to diagnose technical problems, implement secure coding
practices, and optimize user interactions. These enhancements not only
improved the security and functionality of the login system but also
reinforced key principles in software development and authentication
security.

This artifact serves as a strong representation of real-world software
engineering challenges and solutions. By systematically improving
authentication workflows, resolving critical security and usability
issues, and ensuring best practices in API communication, this
authentication system now provides a seamless, secure, and user-friendly
experience. The knowledge gained from these enhancements will continue
to inform future developments in web authentication security and system
optimization.
