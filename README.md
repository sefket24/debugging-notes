# Debugging Notes

This repo is part of my application for the Fly.io Support Engineer role.

A collection of real issues I ran into while working on small projects and deployments, along with how I approached fixing them.

---

## 1. App failed to deploy (Vercel)

**Issue**  
Deployment failed during the build step.

**What I checked**  
- Vercel build logs  
- Local build vs production build  
- Environment variables  

**Fix**  
A required environment variable was missing in production. Added it in Vercel settings and redeployed.

**Takeaway**  
Always compare local and production environments first. Missing environment variables are a common cause of failures.

---

## 2. Domain not resolving correctly

**Issue**  
Custom domain wasn’t loading after setup.

**What I checked**  
- DNS records  
- Domain provider settings  
- Propagation status  

**Fix**  
DNS records were pointing to the wrong target. Updated them and waited for propagation.

**Takeaway**  
Start with DNS when dealing with domain issues. Most problems come from configuration, not code.

---

## 3. Route returning 404 in production

**Issue**  
Route worked locally but returned 404 in production.

**What I checked**  
- File structure  
- Routing configuration  
- Case sensitivity differences  

**Fix**  
File naming mismatch caused the issue in a case-sensitive production environment.

**Takeaway**  
Production environments are stricter than local. File naming and paths need to be exact.

---

## Why I’m documenting this

I’ve spent the last few years in support, and I’m intentionally getting closer to the systems side. I like understanding why things break and how to fix them, not just responding to tickets.
