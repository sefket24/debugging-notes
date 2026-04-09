# Debugging Notes (Fly.io Support Engineer Application)

This repo is part of my application for the Fly.io Support Engineer role.

A collection of real issues I ran into while working on small projects and deployments, along with how I approached fixing them.

## How I approach debugging

When something breaks, I start by checking logs and trying to understand whether the issue is coming from code, environment, or configuration. From there, I narrow things down step by step before jumping to a fix.

---

## 1. App failed to deploy (Vercel)

**Issue**  
Deployment failed during the build step.

**What I checked**  
- Looked at Vercel build logs to determine if this was a code issue or environment issue  
- Compared local build behavior with production  
- Checked environment variables in both environments  

**Fix**  
A required environment variable was missing in production. Added it in Vercel settings and redeployed.

**Takeaway**  
Always compare local and production environments first. Missing environment variables are a common cause of failures.

---

## 2. Domain not resolving correctly

**Issue**  
Custom domain wasn’t loading after setup.

**What I checked**  
- Verified DNS records to confirm traffic was pointing correctly  
- Reviewed domain provider settings to ensure correct configuration  
- Checked propagation status to verify if changes had propagated globally  

**Fix**  
DNS records were pointing to the wrong target. Updated them and waited for propagation.

**Takeaway**  
Start with DNS when dealing with domain issues. Most problems come from configuration, not code.

---

## 3. Route returning 404 in production

**Issue**  
Route worked locally but returned 404 in production.

**What I checked**  
- Examined file structure to ensure paths matched expectations  
- Checked routing configuration to verify exact setup  
- Investigated case sensitivity differences between local and production file systems  

**Fix**  
File naming mismatch caused the issue in a case-sensitive production environment.

**Takeaway**  
Production environments are stricter than local. File naming and paths need to be exact.

---

## 4. App not starting due to port issue

**Issue**  
Application failed to start locally.

**What I checked**  
- Checked which port the app was trying to use  
- Looked for conflicts with other running processes  

**Fix**  
Another process was already using the port. Stopped the conflicting process and restarted the app.

**Takeaway**  
Port conflicts are easy to miss. Always check if something else is already running.

---

## Why I’m documenting this

I’ve spent the last few years in support, and I’m intentionally getting closer to the systems side. I like understanding why things break and how to fix them, not just responding to tickets.
