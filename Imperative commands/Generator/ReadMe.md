# Generator Commands
## Basic
1. kubectl run --generator=run/v1 deploy --dry-run -o yaml --image=nginx 
2. kubectl run --generator=run-pod/v1 deploy --dry-run -o yaml --image=nginx

## Alias for exam
```
alias g='kubectl run --generator=$v deploy --dry-run -o yaml --image=nginx -l label=my-label'
```
1. **Replication Controller:** `v=run/v1 && g`
2. **Deployment:** `unset v && g`
3. **Pods:** `v=run-pod/v1 && g`
4. **Job:** `v=job/v1 && g`
