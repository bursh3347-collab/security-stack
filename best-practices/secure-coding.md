# Secure Coding Best Practices

> Security patterns extracted from Semgrep rules, OWASP guidelines, and real-world vulnerabilities.

## 1. Input Validation

```typescript
// ❌ BAD: Trust user input
const query = `SELECT * FROM users WHERE id = ${req.params.id}`;

// ✅ GOOD: Parameterized query (Drizzle ORM)
const user = await db.select().from(users).where(eq(users.id, req.params.id));

// ✅ GOOD: Zod validation
import { z } from 'zod';
const UserInput = z.object({
  email: z.string().email(),
  name: z.string().min(1).max(100),
});
const validated = UserInput.parse(req.body);
```

## 2. Authentication

```typescript
// ✅ Use established auth libraries
// - Supabase Auth (built-in)
// - Auth.js (NextAuth)
// - Better Auth
// - Clerk / Auth0 (managed)

// ❌ NEVER roll your own auth
// ❌ NEVER store passwords in plain text
// ❌ NEVER use MD5/SHA1 for passwords
```

## 3. API Security

```typescript
// Rate limiting
import { Ratelimit } from '@upstash/ratelimit';
const ratelimit = new Ratelimit({ redis, limiter: Ratelimit.slidingWindow(10, '10 s') });

// CORS configuration
const corsHeaders = {
  'Access-Control-Allow-Origin': process.env.ALLOWED_ORIGIN,
  'Access-Control-Allow-Methods': 'GET, POST',
  'Access-Control-Allow-Headers': 'Content-Type, Authorization',
};

// API key validation
const apiKey = req.headers['x-api-key'];
if (!apiKey || apiKey !== process.env.API_KEY) {
  return new Response('Unauthorized', { status: 401 });
}
```

## 4. Environment Variables

```bash
# .env.local (NEVER commit this)
DATABASE_URL=postgresql://...
STRIPE_SECRET_KEY=sk_live_...
OPENAI_API_KEY=sk-...

# .env.example (commit this — no real values)
DATABASE_URL=postgresql://user:password@localhost:5432/mydb
STRIPE_SECRET_KEY=sk_test_...
OPENAI_API_KEY=sk-...
```

## 5. Dependency Security

```bash
# Check for known vulnerabilities
npm audit
pnpm audit

# Auto-fix
npm audit fix

# Use Dependabot (auto-configured on GitHub)
# Or Renovate for more control
```

## 6. Content Security Policy

```typescript
// next.config.js
const securityHeaders = [
  { key: 'X-Content-Type-Options', value: 'nosniff' },
  { key: 'X-Frame-Options', value: 'DENY' },
  { key: 'X-XSS-Protection', value: '1; mode=block' },
  { key: 'Referrer-Policy', value: 'strict-origin-when-cross-origin' },
];
```

## 7. Semgrep Rules for TypeScript

```yaml
# .semgrep.yml
rules:
  - id: no-eval
    pattern: eval(...)
    message: "eval() is dangerous — use safer alternatives"
    severity: ERROR
    languages: [typescript, javascript]

  - id: no-innerhtml
    pattern: $X.innerHTML = $Y
    message: "innerHTML can lead to XSS — use textContent or a sanitizer"
    severity: WARNING
    languages: [typescript, javascript]
```

## Sources
- OWASP Top 10 (2021)
- Semgrep rule registry
- Next.js security documentation
- Supabase Row Level Security guide
