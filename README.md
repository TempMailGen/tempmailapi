One of Best temporary email generator with reply and forward feature. Our temp email api is helping you to get unlimited tempmails . Just setup API and use on your own [tempmail](https://tempmailgen.com) projects. Use temporary email generator today and get rid of being a victim of email spam. Tempmailgen is your no1 choice to prevent email spam. Also you can use this to create social media accounts like temp mail for facebook,twitter,Netflix and any other unknown site signup.Then throwaway that temp mail.Simply as that.



This API purpose is to help independent developers to automate their work and create own apps and services that require temporary email functionality.


How it works:
Generate any email address by using our domain names
Sign up on sites that require confirmation by mail
The site sends email to the address you specify.
Message comes to our SMTP server, processed and added to the database.
You make a request to the API with login and domain part of email address.
You get a list of emails.
You make a request to the API with message ID, login and domain part of email address to get message details (body, subject, date, attachments etc)


Basic usage:
All request should be send via HTTP GET to this endpoint: https://tempmailgen.com/api/ Response in JSON for all request except download attachment.

Checking your mailbox:

```

To check and get a list of emails for a mailbox demo_api@tempmailgen.com:  https://tempmailgen.com/api/getMessages?username=demo_api&domain=tempmailgen.com

HTTP GET parameters:
Param name	                    Value
url	                            getMessages
username	                    demo_api (username)
domain	                        tempmailgen.com (domain)


Sample output:



  {
    "success": true,
    "message": "Request success",
    "result": {
      "total": 4,
      "email": [
        {
          "email_id": "1",
          "from": "test@gmail.net",
          "date": "2019-10-01 07:55:08",
          "subject": "Test with attachments "
        },
        {
          "email_id": "2",
          "from": "test2@gmail.net",
          "date": "2019-10-02 06:50:02",
          "subject": "Test without attachments "
        },

      ]
    }
  }



Response fields:
success	                Response status
message	                Response details
result	                Object of result variables
total	                Count of emails
email	                Array of email objects
email_id	            Message id
from	                Sender email address
date	                Receive date
subject	                Subject

```

Fetching email:

```
To fetch single email use the following API call : https://tempmailgen.com/api/fetchMessage?username=demo_api&domain=tempmailgen.com&email_id=1

HTTP GET parameters:
Param name                  Value
url	                        fetchMessage
username	                demo_api (username)
domain	                    tempmailgen.com (domain)
email_id	                1 (email_id from getMessages response)


Sample output:

{
  "success": true,
  "message": "Request success",
  "result": {
    "email_id": "1",
    "from": [
      {
        "display": "Sender Name",
        "address": "test@gmail.net",
        "is_group": false
      }
    ],
    "to": [
      {
        "display": "demo_api@tempmailgen.com",
        "address": "demo_api@tempmailgen.com",
        "is_group": false
      }
    ],
		"date":	"Tue, 1 Oct 2019 10:55:08 +0300".
    "subject": "Test with attachments ",
    "html_body": "",
    "text_body": "this letter with attachments\r\n\r\n\r\n",
    "attachments": [
      {
        "file_name": "2019 08 07.pdf",
        "content_type": "application/pdf",
        "size": 1167278
      },
      {
        "file_name": "2019-07-26 1225.jpg",
        "content_type": "image/jpeg",
        "size": 100518
      }
    ]
  }
}



Response fields:

success	       Response status
message	       Response details
result	       Object of result variables
email_id	   Message id
from	       Array of sender email variables
to	           Array of receiver email variables
date	       Receive date
subject	       Email subject
html_body	   Html content of email
text_body	   Text content of email
attachments	   Array of attachments


```

Download attachment:

```

To download email attachment use the following API call : https://tempmailgen.com/api/downloadAttachment?email_id=1&file_name=2019-07-26 1225.jpg

HTTP GET parameters:
Param name	Value
url	        downloadAttachment
email_id	1 (email_id from getMessages or fetchMessage response)
file_name	2019-07-26 12.30.25.jpg (attachment file_name from fetchMessage response)

```
