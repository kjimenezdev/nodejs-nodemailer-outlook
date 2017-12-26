# NodeJS Nodemailer Outlook

Simple integration between node js and outlook.office365 emailing servers this project depends on [Nodemailer](https://nodemailer.com) library overriding its variables with `outlook.office365` defaults.
## Getting Started
Install module using following command :
```
npm install nodejs-nodemailer-outlook
```
In your file.js run the following

```javascript
var nodeoutlook = require('nodejs-nodemailer-outlook')
nodeoutlook.sendEmail({
    auth: {
        user: "johnexample@organization.com",
        pass: "johnpassword"
    }, from: 'info@myorganization.com',
    to: 'jackexample@organization.com',
    subject: 'Hey you, awesome!',
    html: '<b>This is bold text</b>',
    text: 'This is text version!',
    attachments: [
                        {
                            filename: 'text1.txt',
                            content: 'hello world!'
                        },
                        {   // binary buffer as an attachment
                            filename: 'text2.txt',
                            content: new Buffer('hello world!','utf-8')
                        },
                        {   // file on disk as an attachment
                            filename: 'text3.txt',
                            path: '/path/to/file.txt' // stream this file
                        },
                        {   // filename and content type is derived from path
                            path: '/path/to/file.txt'
                        },
                        {   // stream as an attachment
                            filename: 'text4.txt',
                            content: fs.createReadStream('file.txt')
                        },
                        {   // define custom content type for the attachment
                            filename: 'text.bin',
                            content: 'hello world!',
                            contentType: 'text/plain'
                        },
                        {   // use URL as an attachment
                            filename: 'license.txt',
                            path: 'https://raw.github.com/nodemailer/nodemailer/master/LICENSE'
                        },
                        {   // encoded string as an attachment
                            filename: 'text1.txt',
                            content: 'aGVsbG8gd29ybGQh',
                            encoding: 'base64'
                        },
                        {   // data uri as an attachment
                            path: 'data:text/plain;base64,aGVsbG8gd29ybGQ='
                        },
                        {
                            // use pregenerated MIME node
                            raw: 'Content-Type: text/plain\r\n' +
                                 'Content-Disposition: attachment;\r\n' +
                                 '\r\n' +
                                 'Hello world!'
                        }
                    ]
});
```
<b>Options :</b>

- ```auth``` (<span style='color:red;'>Required</span>): JSON object contains two keys `user` and `pass` these are the authentication of the sender account on email server ex: `{"user":"exampl@mail.com","pass":"123456"}`

- ```host``` (<span style='color:red;'>Required</span>) : Server host url, <b>Default</b> : `smtp.office365.com`
- ```port``` (<span style='color:red;'>Required</span>) : Server port, <b>Default</b> : `587`
- ```secure``` (<span style='color:red;'>Required</span>) : false for TLS - as a boolean not string

- ```to```  (<span style='color:red;'>Required</span> if no `cc` or `bcc` are provided): Comma separated emails represent the target recipients.
- ```cc```  (<span style='color:red;'>Required</span> if no `to` or `bcc` are provided): Comma separated emails represent the target carbon copy (CC) recipients.
- ```bcc```  (<span style='color:red;'>Required</span> if no `to` or `cc` are provided): Comma separated emails represent the target blind carbon copy (BCC) recipients.
- ```subject```  (Optional): Email subject.
- ```text```  (Optional): Email text body version.
- ```html```  (Optional): Email html body version.
- ```attachments```  (Optional): JSON array of attachments.
## Built With

* [Nodemailer](https://nodemailer.com) - module for Node.js applications to allow easy as cake email sending. The project got started back in 2010 when there was no sane option to send email messages, today it is the solution most Node.js users turn to by default.

## Versioning

Current version : 1.0.6

## Authors

* **Youans Ezzat**

## Links

[Github](https://github.com/Youans/nodejs-nodemailer-outlook)

[Nodemailer](https://www.npmjs.com/package/nodejs-nodemailer-outlook)

## License

This project is opensource.
