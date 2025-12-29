---
title: JWT Authentication
---

JSON Web Tokens (JWT) are a compact, URL-safe means of representing claims to be transferred between two parties. They are commonly used for authentication and authorization in web applications.

## BEST PRACTICEs for JWT Authentication

You should:

- Store refresh token in HTTP-only cookie (secure, not JS-accessible)
- Store access token in memory only (disappears on refresh)
- Call session check on app startup (before rendering routes)
- Use refresh token to get new access token when needed
- Never check localStorage/sessionStorage for "am I logged in?"
