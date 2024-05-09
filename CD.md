# CD
## Check code works
1. Create ec2 instance
2. Allow 8080 22 for now (we will need port 80 and 3000 later)
3. SSH in and run these commands
```bash
cd app
npm install
npm test
```
## Automate this by getting jenkins to push code
1. Automate SSH into instance