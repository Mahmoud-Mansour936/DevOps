# Notes

## Major steps to deckorize code

1. Specify needed image 
2. Specify needed packages (from requirements, Json file, etc.)
3. Define env variables and ports 
4. Build code 
5. Run code (usually it was in another stage to decrease using space)

## Optimize size

1. Smaller images
2. Multistage docker file 
3. use .dockerignore file
4. Remove unneeded cache (different along the programming languages)

## Some notes for node code

```markdown
1. **NODE_ENV trap**  
   - If set in builder before installing, build fails (no TypeScript).

2. **Express in devDependencies trap**  
   - If `express` mistakenly in devDeps → runtime crash.

3. **Wrong CMD**  
   - Using `npm run start` in runtime adds bloat. Must be direct `node`.

4. **Root user**  
   - `/whoami` returns `uid:0` → fail.

5. **Cache misuse**  
   - Copying code before `npm install` → breaks cache.

6. **Healthcheck**  
   - Wrong command/host → container unhealthy.
```

## Errors

- The source in COPY instruction must be from build-context (./blabla)