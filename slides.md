---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: "text-center"
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Deno 2.0: A Modern Runtime for JavaScript and TypeScript
  Presentation slides for developers.
# persist drawings in exports and build
drawings:
  persist: false
# use UnoCSS
css: unocss
---

# Welcome to Deno 2.0

A secure and modern runtime for JavaScript and TypeScript

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <a href="https://deno.land" target="_blank" alt="Deno Website"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---

# What is Deno?

Deno is a modern runtime for JavaScript and TypeScript that aims to address Node.js's shortcomings:

- 🔒 **Secure by default** - No file, network, or environment access, unless explicitly enabled
- 📦 **TypeScript out of the box** - Native support without additional tooling
- 📚 **Standard library** - Comprehensive set of standard modules
- 🌐 **URL-based module imports** - No package manager required
- 🚀 **Easy to install and use** - Single executable
- 🔧 **Built-in development tools** - Linter, formatter, and debugger included

<br>

Read more about [Why Deno?](https://deno.land/manual@v1.31.1/introduction)

---

# Challenges in Node.js

<div grid="~ cols-2 gap-4">
<div>

## Module System Issues

- Complex `package.json` and `node_modules`
- Dependency hell
- Bloated project size

## TypeScript Integration

- Lack of native support
- Additional tooling required
- Complex setup and configuration

</div>
<div>

## Security Concerns

- Unrestricted access by default
- Potential risks from untrusted packages
- Difficult to control permissions

## Performance

- Built on C++ and JavaScript (V8 engine)
- Room for improvement in efficiency

</div>
</div>

---

# How Deno 2.0 Addresses These Issues

<div grid="~ cols-2 gap-4">
<div>

## Modern Module System

- ES modules and URL-based imports
- No `node_modules` or `package.json`
- Simplified dependency management

```typescript
import { serve } from "https://deno.land/std/http/server.ts";
```

## Native TypeScript Support

- Out-of-the-box TypeScript support
- No additional configuration needed
- Streamlined development process

</div>
<div>

## Security-first Approach

- Sandboxed execution model
- Explicit permission granting
- Enhanced application security

```bash
deno run --allow-net my_script.ts
```

## Performance Boost with Rust

- Written in Rust for efficiency
- Improved memory management
- Better handling of concurrent operations

</div>
</div>

---

# Key Features of Deno 2.0

<div grid="~ cols-2 gap-4">
<div>

## Backward Compatibility

- Run existing Node.js applications
- Use popular npm packages
- Smooth transition for developers

## Package Management with `jsr`

- New package registry for TypeScript and Deno
- Improved dependency management
- Support for versioning and caching

</div>
<div>

## Improved CLI Commands

- `deno install` for executable scripts
- `deno run` with permission flags
- `deno compile` for standalone binaries

## API Enhancements

- `Deno.serve` for HTTP servers
- `Deno.openKv` for key-value store operations
- Streamlined and performant APIs

</div>
</div>

---

# Code Example: HTTP Server

```typescript {all|1|3-5|7-9|11-12}
import { serve } from "https://deno.land/std@0.140.0/http/server.ts";

function handler(req: Request): Response {
  const url = new URL(req.url);

  if (url.pathname === "/") {
    return new Response("Welcome to Deno 2.0!");
  }

  return new Response("Not Found", { status: 404 });
}

console.log("HTTP server running on http://localhost:8000");
await serve(handler, { port: 8000 });
```

Run with: `deno run --allow-net server.ts`

---

# Testing in Deno

Deno comes with a built-in testing framework:

```typescript
import { assertEquals } from "https://deno.land/std@0.140.0/testing/asserts.ts";

Deno.test("hello world", () => {
  const x = 1 + 2;
  assertEquals(x, 3);
});

Deno.test("async hello world", async () => {
  const x = await Promise.resolve(1 + 2);
  assertEquals(x, 3);
});
```

Run tests with: `deno test`

---

# Use Cases for Deno 2.0

<div grid="~ cols-2 gap-4">
<div>

## Secure Server-side Applications

- Strict access controls
- Ideal for handling sensitive data
- Minimized risk of unauthorized access

## TypeScript-heavy Projects

- Seamless TypeScript integration
- Simplified setup and configuration
- Improved developer experience

</div>
<div>

## Microservices and Serverless Functions

- Lightweight runtime
- Performance optimizations
- Efficient for small, focused services

## Front-end Development Tools

- Modern module system
- Built-in tooling
- Improved security practices

</div>
</div>

---

# Deno Deploy

- Serverless JavaScript deployment platform
- Run Deno applications at the edge
- Seamless integration with Deno runtime

```typescript
import { serve } from "https://deno.land/std@0.140.0/http/server.ts";

serve((req) => new Response("Hello from Deno 2.0 Deploy!"));

console.log("HTTP server running on http://localhost:8000");
```

Deploy directly from your GitHub repository or using the `deployctl` CLI tool.

---

layout: center
class: text-center

---

# Learn More

[Deno Documentation](https://deno.land/manual) · [Deno Standard Library](https://deno.land/std) · [Deno Deploy](https://deno.com/deploy)
