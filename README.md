<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://placehold.co/900x240/111827/FFFFFF/png?text=Supermail&font=raleway">
    <img src="https://placehold.co/900x240/F9FAFB/111827/png?text=Supermail&font=raleway" alt="Supermail — Email API for developers" width="100%">
  </picture>

  <h1>Supermail</h1>

  <p><strong>Email infrastructure for developers. Simple API. Your applications.</strong></p>

  <p>
    <a href="https://github.com/YOUR_USERNAME/supermail/stargazers">
      <img src="https://img.shields.io/github/stars/YOUR_USERNAME/supermail?style=flat-square&logo=github&label=Stars" alt="GitHub stars">
    </a>
    <a href="https://github.com/YOUR_USERNAME/supermail/network/members">
      <img src="https://img.shields.io/github/forks/YOUR_USERNAME/supermail?style=flat-square&logo=github&label=Forks" alt="GitHub forks">
    </a>
    <a href="./LICENSE">
      <img src="https://img.shields.io/github/license/YOUR_USERNAME/supermail?style=flat-square" alt="MIT License">
    </a>
    <a href="https://github.com/YOUR_USERNAME/supermail/commits/main">
      <img src="https://img.shields.io/github/last-commit/YOUR_USERNAME/supermail?style=flat-square" alt="Last commit">
    </a>
    <img src="https://img.shields.io/badge/status-in%20development-orange?style=flat-square" alt="Project status">
  </p>

  <p>
    <a href="#about">About</a> ·
    <a href="#features">Features</a> ·
    <a href="#technology-stack">Tech Stack</a> ·
    <a href="#getting-started">Getting Started</a> ·
    <a href="#environment-variables">Environment Variables</a> ·
    <a href="#api-usage">API Usage</a> ·
    <a href="#roadmap">Roadmap</a> ·
    <a href="#contributing">Contributing</a>
  </p>
</div>

---

## Table of Contents

- [About](#about)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Dependencies](#dependencies)
- [Environment Variables](#environment-variables)
- [Database Setup](#database-setup)
- [Authentication](#authentication)
- [API Usage](#api-usage)
- [Security](#security)
- [Deployment](#deployment)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Security Reports](#security-reports)
- [License](#license)

## About

**Supermail** is an email API platform designed to help developers integrate email delivery into their applications through a straightforward API.

The project is being developed around a modern TypeScript stack, PostgreSQL database infrastructure, authentication, and BunMail as the planned email delivery engine.

Supermail aims to provide a centralized place to manage API access, integrate email delivery, and build developer-friendly email workflows.

> **Development status:** Supermail is under active development. Features described as planned or in progress are not necessarily available yet. API routes, deployment configuration, and production readiness must be verified as implementation progresses.

## Features

### Planned platform features

- **Developer-focused API:** Send emails from applications using HTTP requests.
- **API key management:** Give applications their own credentials for accessing Supermail.
- **Authentication:** User accounts, sessions, and email verification.
- **Email delivery integration:** Connect Supermail to the BunMail sending engine.
- **Dashboard:** Manage account settings, API credentials, and email activity.
- **Database-backed platform:** Store account and application data in PostgreSQL.
- **Usage tracking:** Build visibility into API usage and delivery activity.
- **Email templates:** Support reusable email content.
- **Sender domains:** Work toward configurable sender identities and domain verification.
- **Security controls:** Plan for request validation, rate limiting, authorization, and secret protection.

Features will be marked available as they are implemented and tested.

## Technology Stack

| Technology | Purpose |
|---|---|
| [Next.js](https://nextjs.org/) | Web application framework |
| [React](https://react.dev/) | User interface |
| [TypeScript](https://www.typescriptlang.org/) | Type-safe application development |
| [Tailwind CSS](https://tailwindcss.com/) | Interface styling |
| [Better Auth](https://www.better-auth.com/) | Authentication and sessions |
| [Neon](https://neon.tech/) | Serverless PostgreSQL database |
| [Drizzle ORM](https://orm.drizzle.team/) | Database queries and schema management |
| [Bun](https://bun.sh/) | Runtime and package management for compatible services |
| [BunMail](https://github.com/mohamedboukari/bunmail) | Planned email delivery engine |
| [Deno Deploy](https://deno.com/deploy) | Planned hosting target, subject to compatibility testing |

### Technology logos

<div align="center">
  <a href="https://nextjs.org/"><img src="https://skillicons.dev/icons?i=nextjs" alt="Next.js" height="42"></a>
  <a href="https://www.typescriptlang.org/"><img src="https://skillicons.dev/icons?i=ts" alt="TypeScript" height="42"></a>
  <a href="https://react.dev/"><img src="https://skillicons.dev/icons?i=react" alt="React" height="42"></a>
  <a href="https://tailwindcss.com/"><img src="https://skillicons.dev/icons?i=tailwind" alt="Tailwind CSS" height="42"></a>
  <a href="https://bun.sh/"><img src="https://skillicons.dev/icons?i=bun" alt="Bun" height="42"></a>
  <a href="https://www.postgresql.org/"><img src="https://skillicons.dev/icons?i=postgres" alt="PostgreSQL" height="42"></a>
</div>

## Architecture

Supermail is planned as a web platform that communicates with a separate email delivery service.

```text
Developer Application
        |
        | HTTPS API request
        v
     Supermail API
        |
        +---- Authentication and API key checks
        |
        +---- Request validation and usage limits
        |
        +---- Neon PostgreSQL
        |
        v
    BunMail Service
        |
        v
    Email Delivery
```

The diagram describes the intended architecture, not a claim that every component is currently deployed or operational.

## Getting Started

### Prerequisites

Install or create the following before running the application:

- [Git](https://git-scm.com/downloads)
- [Bun](https://bun.sh/) for package management and compatible tooling
- [Node.js](https://nodejs.org/) for the Next.js development environment, where required by the selected tooling
- A [Neon](https://neon.tech/) PostgreSQL project
- A Better Auth secret
- Access to a BunMail service for testing email delivery

You do not need Google OAuth credentials until Google sign-in is implemented and enabled.

### 1. Clone the repository

Replace `YOUR_USERNAME` with the GitHub account or organization that owns the repository.

```bash
git clone https://github.com/YOUR_USERNAME/supermail.git
cd supermail
```

### 2. Install dependencies

If the repository contains a `bun.lock` or `bun.lockb` file and uses Bun:

```bash
bun install
```

If the project instead uses npm and has a `package-lock.json`:

```bash
npm install
```

Use the package manager and lockfile committed to the repository. Do not mix package managers without intentionally migrating the lockfile.

### 3. Configure environment variables

Create a local `.env` file using `.env.example` as a reference.

```bash
cp .env.example .env
```

Fill in the values for the services you have configured. See [Environment Variables](#environment-variables) for descriptions.

**Never commit `.env` or real API keys to GitHub.**

### 4. Configure the database

Create a PostgreSQL database in Neon and copy its connection string into `DATABASE_URL`.

Once the Drizzle schema and migrations are implemented, run the repository's database migration command. The example command below assumes a Drizzle configuration and migration setup exist:

```bash
bunx drizzle-kit generate
bunx drizzle-kit migrate
```

If migrations have not yet been created, these commands will not initialize a complete application schema.

### 5. Start the development server

Use the script defined in `package.json`:

```bash
bun run dev
```

For an npm-based installation:

```bash
npm run dev
```

The local application is typically available at:

```text
http://localhost:3000
```

The application cannot provide working authentication, database access, or email delivery until those integrations are configured and implemented.

## Dependencies

The final dependency list should be maintained in `package.json` and pinned through the committed lockfile.

The planned dependency groups are:

| Dependency | Purpose |
|---|---|
| `next` | Web framework |
| `react` | UI rendering |
| `react-dom` | React DOM rendering |
| `typescript` | Type checking |
| `tailwindcss` | Utility-first CSS |
| `@tailwindcss/postcss` | Tailwind CSS integration with PostCSS |
| `@types/node` | Node.js type definitions |
| `@types/react` | React type definitions |
| `@types/react-dom` | React DOM type definitions |
| `eslint` | Code linting |
| `eslint-config-next` | Next.js linting rules |
| `better-auth` | Authentication |
| `drizzle-orm` | Database ORM |
| `drizzle-kit` | Database schema and migration tooling |
| `@neondatabase/serverless` | Neon PostgreSQL connectivity |

Additional dependencies may be required as the implementation develops, including email validation, schema validation, rate limiting, logging, testing, and API documentation tooling.

This table describes the planned stack, not a substitute for checking the repository's actual `package.json`. Use compatible, currently supported versions when installing dependencies.

## Environment Variables

Create `.env.example` in the repository root with the following variables:

```dotenv
# Application
NODE_ENV=development
SUPERMAIL_PUBLIC_BASE_URL=http://localhost:3000

# Database
DATABASE_URL=

# Authentication
BETTER_AUTH_SECRET=
BETTER_AUTH_URL=http://localhost:3000

# Google OAuth — optional until enabled
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=

# BunMail email delivery service
BUNMAIL_BASE_URL=
BUNMAIL_API_KEY=

# API key security
SUPERMAIL_API_KEY_PEPPER=
```

### Variable reference

| Variable | Required when | Description |
|---|---|---|
| `NODE_ENV` | Running the application | Environment mode, such as `development` or `production` |
| `SUPERMAIL_PUBLIC_BASE_URL` | Building absolute application URLs | Public base URL for the Supermail application |
| `DATABASE_URL` | Database features are enabled | PostgreSQL connection string supplied by Neon |
| `BETTER_AUTH_SECRET` | Authentication is enabled | Strong, private secret used by Better Auth |
| `BETTER_AUTH_URL` | Authentication is enabled | Base URL used by Better Auth |
| `GOOGLE_CLIENT_ID` | Google OAuth is enabled | OAuth client ID from Google Cloud |
| `GOOGLE_CLIENT_SECRET` | Google OAuth is enabled | Private OAuth client secret |
| `BUNMAIL_BASE_URL` | BunMail integration is enabled | Base URL of the BunMail service |
| `BUNMAIL_API_KEY` | BunMail integration is enabled | Credential used to authenticate with BunMail |
| `SUPERMAIL_API_KEY_PEPPER` | If the API-key hashing implementation uses a pepper | Server-side secret used in API-key verification |

### Environment variable security

- Use different credentials for development and production.
- Generate a cryptographically strong authentication secret.
- Keep OAuth client secrets and service API keys private.
- Never place private credentials in client-side code or variables exposed to the browser.
- Configure production variables in the hosting provider's secret or environment-variable settings.
- Do not invent a value for a missing service credential; obtain it from the corresponding provider.
- Only require optional variables when the associated feature is enabled.

The final application configuration should validate required variables at startup and provide clear errors for missing or malformed values.

## Database Setup

Supermail is planned to use Neon PostgreSQL with Drizzle ORM.

The database will eventually store records such as:

- User accounts and authentication data
- API keys and their metadata
- Email request records
- Delivery statuses and provider responses
- Usage and quota information
- Sender domains and verification states
- Email templates
- Relevant audit and security events

The actual schema should be defined in the source code and applied through version-controlled migrations.

Do not assume these tables exist until their schemas and migrations have been added to the repository.

## Authentication

Authentication is planned around Better Auth.

Planned capabilities include:

- User registration and sign-in
- Session management
- Email verification by code and link
- Account settings
- Google OAuth as a later integration

Authentication routes and email verification workflows must be implemented and tested before these features can be considered available.

## API Usage

Supermail is intended to expose an HTTP API for applications that need to send email.

### Planned send-email request

The following illustrates the intended request shape. It is an example of the proposed integration, not a guarantee that the Supermail endpoint is already implemented.

```bash
curl -X POST "https://YOUR_SUPERMAIL_API_HOST/v1/emails" \
  -H "Authorization: Bearer YOUR_SUPERMAIL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "from": "hello@example.com",
    "to": ["recipient@example.com"],
    "subject": "Hello from Supermail",
    "text": "Your email integration is ready."
  }'
```

The final endpoint, request schema, response format, and authentication behavior must be documented against the implemented API.

### Planned API requirements

- HTTPS for production requests
- API key authentication
- Input and recipient validation
- Sender identity and domain checks
- Rate limits and usage quotas
- Authorization and resource ownership checks
- Consistent error responses
- Safe retry behavior and idempotency where appropriate
- Delivery status tracking
- Protection against API key leakage

Never use a real production API key in a public README example.

## Security

Security is a core requirement for an email API platform.

The implementation should include:

- Secure handling of authentication secrets
- Hashed or otherwise securely protected API keys
- Authorization checks on user-owned resources
- Input validation and output handling
- Rate limiting and abuse prevention
- Protection against unauthorized sender identities
- Safe logging that avoids credentials and sensitive email content
- Dependency updates and vulnerability checks
- HTTPS and production secret management

Security features should only be described as implemented after they have been verified in code and tested.

## Deployment

Supermail's planned web hosting target is Deno Deploy, subject to compatibility testing.

Before production deployment:

1. Confirm the Next.js version and deployment adapter or runtime requirements.
2. Test database connectivity from the selected runtime.
3. Verify Better Auth session and cookie behavior.
4. Test every required environment variable.
5. Confirm the BunMail service can be reached securely.
6. Verify that email sending, error handling, and retries work end to end.
7. Configure production secrets and HTTPS.
8. Test rate limits, API key protection, and authorization.
9. Run the production build and application tests.

BunMail may require separate hosting because its runtime, framework, networking, and outbound SMTP requirements may differ from the Supermail web application's requirements.

Deployment is not considered production-ready until these checks pass.

## Roadmap

- [ ] Establish the Next.js, React, TypeScript, and Tailwind CSS foundation
- [ ] Add repository scripts, linting, and type checking
- [ ] Configure Neon PostgreSQL
- [ ] Define database schemas and migrations with Drizzle
- [ ] Implement Better Auth registration and sessions
- [ ] Add email verification by code and link
- [ ] Evaluate Google OAuth integration
- [ ] Test BunMail compatibility and service connectivity
- [ ] Implement a secure BunMail delivery adapter
- [ ] Build API key creation, storage, and revocation
- [ ] Implement the public email API
- [ ] Add validation, quotas, and rate limits
- [ ] Build the account dashboard
- [ ] Add email templates and sender-domain workflows
- [ ] Implement usage tracking and delivery history
- [ ] Add automated tests and security checks
- [ ] Verify Deno Deploy compatibility
- [ ] Launch a private beta
- [ ] Prepare the public launch

The roadmap may change as implementation and compatibility testing progress.

## Contributing

Contributions, bug reports, and thoughtful feature suggestions are welcome.

Before opening a pull request:

1. Check existing issues to avoid duplicating work.
2. Explain the problem or proposed improvement.
3. Keep changes focused and easy to review.
4. Run the available lint, type-check, and test commands.
5. Never include secrets, credentials, or personal data in commits.

For significant changes, open an issue or discussion first so the proposed direction can be reviewed.

## Security Reports

Please do not publish sensitive vulnerability details in a public issue.

Until a dedicated security contact is established, use GitHub's private vulnerability reporting feature if it is enabled for this repository. Otherwise, contact the repository owner privately.

Include enough information to reproduce the issue safely, but do not disclose real API keys, credentials, or private user data.

## Contributors

Contributions will be reflected automatically by GitHub as the project develops.

<a href="https://github.com/YOUR_USERNAME/supermail/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=YOUR_USERNAME/supermail" alt="Supermail contributors">
</a>

## Repository Activity

[![Commit activity](https://img.shields.io/github/commit-activity/m/YOUR_USERNAME/supermail?style=flat-square)](https://github.com/YOUR_USERNAME/supermail/graphs/commit-activity)
[![Languages](https://img.shields.io/github/languages/top/YOUR_USERNAME/supermail?style=flat-square)](https://github.com/YOUR_USERNAME/supermail)
[![Issues](https://img.shields.io/github/issues/YOUR_USERNAME/supermail?style=flat-square)](https://github.com/YOUR_USERNAME/supermail/issues)
[![Pull requests](https://img.shields.io/github/issues-pr/YOUR_USERNAME/supermail?style=flat-square)](https://github.com/YOUR_USERNAME/supermail/pulls)

## License

Supermail is licensed under the MIT License.

Copyright (c) 2026 Supermail

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
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

<div align="center">
  <p><strong>Supermail</strong> — Email infrastructure for developers.</p>
  <sub>Built with TypeScript and an API-first mindset.</sub>
</div>
