# Next.js 15 Server Component Dynamic Import Error

This repository demonstrates a subtle bug in Next.js 15 related to dynamic imports within server components. The problem occurs when a function is used for both client and server rendering, and it contains a dynamic import that resolves to a module only available on the server.  This leads to a runtime error on the client.

The `serverComponentBug.js` file shows the problematic code, while `serverComponentBugSolution.js` provides a solution.

## Bug Description
When a server component function attempts to dynamically import a server-only module within a context used by both client and server, a runtime error occurs on the client-side during hydration due to the module's unavailability.  The standard Next.js error messages might not clearly indicate the root cause, making it difficult to diagnose.

## Solution
The solution involves using runtime checks to conditionally execute the dynamic import only on the server.  This prevents the client from attempting to load modules that are not intended for its execution environment.