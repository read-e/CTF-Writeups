# Test
Liam Reidy

**Instructions:** Your task now is to access the test user account but this relic will crash with simple brute-force attempts, instead of guessing, think like a user from the 90s.

I started by downloading the site with `wget` and using `grep` to search for any appearances of `EKO`, but all I got was the flag from [Hidden](../Hidden/hidden-Solution.md).

Thinking like a user from the 90's I tried logging in with these credentials:
```
username: test
password: 123456
```

Sure enough, that was the password for the `test` user account. The flag was displayed on the page `http://microson.ctf.site:20080/#welcome_test_EKO{test_test}`

`EKO{test_test}`
