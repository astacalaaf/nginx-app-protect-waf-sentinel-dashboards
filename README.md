### Introduction

The NGINX App Protect data connector provides the capability to ingest NGINX+ App Protect WAF events into Microsoft Sentinel. Refer to [NGINX+ App Protect log](https://docs.nginx.com/nginx-app-protect-waf/logging-overview/security-log/) documentation for more information.

### Security Log Configuration

- Recommendation log path /var/log/app_protect/policy/*.log
- JSON Config

```json
{
    "filter": {
        "request_type": "all"
    },

    "content": {
        "format": "splunk",
        "max_request_size": "any",
        "max_message_size": "32k",
        "list_delimiter": ";"
    }
}
```

### Diagram

```mermaid
flowchart TD
  NGINX+ -.-> |agent|TBL_NAP(Table Analytics NGINX_NAP_CL) -.-> |visualize|NAP_WB(F5 NGINX App Protect Workbook)
```

### How-to

**Create Log Analytics**

- Log Analytics workspace > Tables > Create > New custom log (MMA-based)
- Upload sample logs from /var/log/app_protect/<nginx-nap>.log

![Untitled](https://user-images.githubusercontent.com/9154599/236676701-fc7252b6-289e-4d88-9fef-708fdd5df165.png)

- Record delimiter new line

![Untitled 1](https://user-images.githubusercontent.com/9154599/236676712-213c1bd3-bff5-494a-9a95-8be23c309928.png)

- Collection type Linux path to /var/log/app_protect/policy/*.log

![Untitled 2](https://user-images.githubusercontent.com/9154599/236676721-a0c2f113-0f69-46e1-8fe4-ca6cfa7a3365.png)

- Custom logs name NGINX_NAP with optional description

![Untitled 3](https://user-images.githubusercontent.com/9154599/236676729-ec5fb160-b1c2-47d2-b462-d07afa9d5e2a.png)

- Create

![Untitled 4](https://user-images.githubusercontent.com/9154599/236676734-f0d32fa9-f8c7-499d-b631-250093dd627a.png)

**Import Workbook**

- Microsoft Sentinel > Workbooks > Add workbook > Edit > Advanced Editor

![Untitled 5](https://user-images.githubusercontent.com/9154599/236676758-727995c7-55f4-432f-b42d-9dba30f89b34.png)

- Apply and save workbook

### Dashboard Preview

![Untitled 6](https://user-images.githubusercontent.com/9154599/236676769-7cedb644-5c04-4fb2-8d10-ad11d065b9f6.png)

![Untitled 7](https://user-images.githubusercontent.com/9154599/236676781-5c40a9fe-02a5-4082-81d7-b923535553e3.png)

![Untitled 8](https://user-images.githubusercontent.com/9154599/236676834-f52cfd7a-4bf8-41d8-9907-106adc4a41d9.png)

![Untitled 9](https://user-images.githubusercontent.com/9154599/236676849-659deded-fe0d-4a56-b808-559b3dba0a11.png)

![Untitled 10](https://user-images.githubusercontent.com/9154599/236676859-3121f73e-5a56-4ffd-8a6d-ebfd86b32132.png)

![Untitled 11](https://user-images.githubusercontent.com/9154599/236676878-fdeaf1d2-cb86-411f-a1b8-d0656a05b775.png)

![Untitled 12](https://user-images.githubusercontent.com/9154599/236676889-bf3c081d-d15f-48ed-b466-87762440099d.png)

![Untitled 13](https://user-images.githubusercontent.com/9154599/236676901-dfbd6219-c08a-4ad5-b67f-9062b4c7ebf5.png)

![Untitled 14](https://user-images.githubusercontent.com/9154599/236676911-d1fb6202-6254-4f10-8640-896bc3f2ee72.png)
