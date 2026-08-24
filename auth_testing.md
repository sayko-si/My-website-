# Auth Testing Playbook

Step 1: MongoDB Verification
```
mongosh
use test_database
db.users.find({role: "admin"}).pretty()
```
Verify: bcrypt hash starts with `$2b$`, unique index on users.email, index on login_attempts.identifier.

Step 2: API Testing
```
curl -c cookies.txt -X POST $API_URL/api/auth/login -H "Content-Type: application/json" -d '{"email":"admin@actqbn.com.au","password":"ActQbn#2026"}'
curl -b cookies.txt $API_URL/api/auth/me
```
Login returns the user object and sets access_token + refresh_token cookies. /me returns the same user.

Step 3: Protected routes
```
curl $API_URL/api/bookings   # expect 401 without cookie
curl -b cookies.txt $API_URL/api/bookings   # expect 200 list
```

Step 4: Brute force — 5 bad logins returns 429 lockout.
