## Grafana

### [reset password](https://grafana.com/docs/grafana/latest/administration/cli/)
```bash
$ curl -X PUT -H "Content-Type: application/json" -d '{
  "oldPassword": "admin",
  "newPassword": "newpass",
  "confirmNew": "newpass"
}' http://admin:admin@<your_grafana_host>:3000/api/user/password
```
