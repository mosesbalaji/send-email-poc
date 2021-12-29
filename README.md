# Action to Onboard Users, send email invites in one shot.

This action makes it easy to onboard users and send invites automatically after validating their email is from '@sc.com' domain. This also triggers consolidated mail to the core wg DL Team.

## Input

- `token` : `required` A Github Personal Access Token for a user that has access to the organisation & repositories.
- `EMAIL` : Email Id of the users to be onboarded in the Organisation.

## Outputs

The Gitub Action will register the following outputs:

- `report_json` : The path to the file containing the JSON Data in which the log of sending emails will be stored.
- `message` : Output of the action taken or an error message if any error occurs.
- `stepStaus` : Success or Failure Information. 



## Example

Invoke the step providing the required parameters to send emails.

```yaml
- name: Send mail
        uses: dawidd6/action-send-mail@v3
        with:
          # Required mail server address:
          server_address: smtp.gmail.com
          # Required mail server port:
          server_port: 465
          # Optional (recommended): mail server username:
          username: ${{secrets.MAIL_USERNAME}}
          # Optional (recommended) mail server password:
          password: ${{secrets.MAIL_PASSWORD}}
          # Required mail subject:
          subject: Test Email trigger by github actions
          # Required recipients' addresses:
          to: ${{env.EMAIL}}
          # Required sender full name (address can be skipped):
          from: pradipta.chatterjee98@gmail.com
          # Optional whether this connection use TLS (default is true if server_port is 465)
          secure: true
          #Optional HTML Body
          html_body: |
              <!DOCTYPE html>
              <html>
              <body>
              <h1 style="color: green">Welcome to Standard Charterd Bank !!</h1>
              <p style="font-family:'Courier New'">Hi User,
              <br>
              <br> You have been successfully Onboarded.
              <br>
              <br>Regards,
              <br>TCS - SCB DevOps Team
              </p>
              </body>
              </html>
          # Optional carbon copy recipients:
          cc: pradipta.chatterjee96@gmail.com
          # Optional blind carbon copy recipients:
          ignore_cert: true
          # Optional converting Markdown to HTML (set content_type to text/html too):
          convert_markdown: true
```
