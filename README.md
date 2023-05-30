# Lightsail Monitor
An AWS Lightsail monitor service that can auto change blocked IP.

### How to use
```yaml
LogLevel: warning # Log level: debug, info, warn, error, fatal, panic
Internal: 300 # Time to check the node connection (unit: second)
Timeout: 15 # Timeout for the tcp request (unit: second)
Concurrent: 20 # Max concurrent on nodes check
DDNS:
  Enable: true
  Provider: cloudflare
  Config:
    CLOUDFLARE_EMAIL: test@test.com
    CLOUDFLARE_API_KEY: YOUR_TOKEN
#  Provider: google
#  Config:
#    GOOGLEDOMAIN_USERNAME: username
#    GOOGLEDOMAIN_PASSWORD: password
Notify:
  Enable: false
  Provider: pushplus
  Config:
    PUSHPLUS_TOKEN: YOUR_TOKEN
#  Provider: telegram
#  Config:
#    TELEGRAM_CHATID: 123
#    TELEGRAM_TOKEN: YOUR_TOKEN
Accounts:
  - AccessKeyID: YOUR_AWS_AccessKeyID
    SecretAccessKey: YOUR_AWS_SecretAccessKey
    Regions:
      - Name: ap-northeast-1 # AWS service endpoints, check https://docs.aws.amazon.com/general/latest/gr/rande.html for help
        Nodes:
          - InstanceName: Debian-1
            Domain: node1.test.com # The node domain
            Port: 8080 # The node port
            Network: tcp4 # The type of network (tcp4, tcp6)

      - Name: ap-southeast-1 # AWS service endpoints, check https://docs.aws.amazon.com/general/latest/gr/rande.html for help
        Nodes:
          - InstanceName: Debian-1
            Domain: node2.test.com # The node domain
            Port: 8080 # The node port
            Network: tcp6 # The type of network (tcp4, tcp6)

#  - AccessKeyID: YOUR_AWS_AccessKeyID_2
#    SecretAccessKey: YOUR_AWS_SecretAccessKey_2
#    Regions:
#      - Name: ap-northeast-1
#        Nodes:
#          - InstanceName: Debian-1
#            Domain: node3.test.com # The node domain
#            Port: 8080 # The node port
#            Network: tcp4 # The type of network (tcp4, tcp6)
#
#      - Name: ap-southeast-1
#        Nodes:
#          - InstanceName: Debian-1
#            Address: node4.test.com # The node domain
#            Port: 8080 # The node port
#            Network: tcp4 # The type of network (tcp4, tcp6)
```
