
### ios
#### [get info from *.plist](https://stackoverflow.com/questions/11307275/how-can-i-find-the-version-number-of-an-iphone-app-from-the-ipa)
```bash
$ /usr/libexec/PlistBuddy -c "Print :CFBundleIdentifier" package/Info.plist
com.philips.cdi.iam.demo

$ /usr/libexec/PlistBuddy -c print package/Info.plist | grep CFBundleVersion
    CFBundleVersion = 185
```

#### get ipa file information
```bash
$ gem install shenzhen
$ ipa info myapp-0.3.0/myapp.ipa
security: SecPolicySetValue: One or more parameters passed to a function were not valid.
+-----------------------------+------------------------------------------------------------------+
| AppIDName                   | mymobileapp                                                      |
| ApplicationIdentifierPrefix | 9BXY7H1234                                                       |
| CreationDate                | 2017-04-13T04:58:51+00:00                                        |
| Platform                    | iOS                                                              |
| Entitlements                | keychain-access-groups: ["9BXY7H1234.*"]                         |
|                             | get-task-allow: false                                            |
|                             | application-identifier: 9BXY7H1234.com.philips.cdi.fpp.mom.pilot |
|                             | com.apple.developer.healthkit: true                              |
|                             | com.apple.developer.team-identifier: 9BXY7H1234                  |
|                             | aps-environment: production                                      |
| ExpirationDate              | 2018-04-13T04:58:51+00:00                                        |
| Name                        | FppMomPilotAppDistribution                                       |
| ProvisionsAllDevices        | true                                                             |
| TeamIdentifier              | 9BXY7H1234                                                       |
| TeamName                    | Philips (China) Investment Co., Ltd                              |
| TimeToLive                  | 365                                                              |
| UUID                        | 4b73738f-d730-49e4-a8eb-0031275cdee4                             |
| Version                     | 1                                                                |
| Codesigned                  | False                                                            |
+-----------------------------+------------------------------------------------------------------+

#### check version

```bash
$ unzip -l myapp-0.3.0/myapp.ipa  | grep mobileprovision
                                 7589  06-30-2017 17:29   Payload/myapp.app/embedded.mobileprovision


$ unzip -p myapp-0.3.0/myapp.ipa "Payload/myapp.app/embedded.mobileprovision" | security cms -D | grep version
security: SecPolicySetValue: One or more parameters passed to a function were not valid.
<?xml version="1.0" encoding="UTF-8"?>
<plist version="1.0">

$ unzip -p myapp-0.3.0/myapp.ipa "Payload/myapp.app/embedded.mobileprovision" | security cms -D | egrep \<key.*Version -A 1 | egrep \<integer
security: SecPolicySetValue: One or more parameters passed to a function were not valid.
        <integer>1</integer>

$ unzip -p myapp-0.3.0/myapp.ipa "Payload/myapp.app/embedded.mobileprovision" | security cms -D | egrep \<key.*Version -A 1 | egrep \<integer | sed -r -e 's:^.*integer>(.*)<.*$:\1:'
security: SecPolicySetValue: One or more parameters passed to a function were not valid.
1

$ unzip -p myapp-0.3.0/myapp.ipa "Payload/myapp.app/embedded.mobileprovision" | security cms -D
security: SecPolicySetValue: One or more parameters passed to a function were not valid.
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
        <key>AppIDName</key>
        <string>myapp</string>
        <key>ApplicationIdentifierPrefix</key>
        <array>
        <string>9BXY7H1234</string>
        </array>
...
```
``````
#### [get uuid](https://gist.github.com/benvium/2568707)

```bash
uuid=$(/usr/libexec/PlistBuddy -c 'Print :UUID' /dev/stdin <<< $(security cms -D -i ${mp})_)

uuid=$(/usr/libexec/PlistBuddy -c 'Print :Entitlements:application-identifier' /dev/stdin <<< $(security cms -D -i ${mp})_)
```

### idevice
```bash
```
