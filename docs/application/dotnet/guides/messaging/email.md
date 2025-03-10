# Email


You can access the email infrastructure to allow the user to exchange digital messages. Email systems are based on a store-and-forward model, in which email server computer systems accept, forward, deliver, and store messages on behalf of users, who only need to connect to the email infrastructure, typically an email server, with a network-enabled device for the duration of message submission or retrieval.

The main feature of the [Tizen.Messaging.Email](/application/dotnet/api/TizenFX/latest/api/Tizen.Messaging.Email.html) namespace is email message sending. You can connect to an email server, and compose, save, and [send email messages](#sending) using SMTP.

The `Tizen.Messaging.Email` namespace can be utilized by any component in the application layer which helps the device user to manage email messaging. For example, the email methods can be invoked by a multimedia module when the user wants to send a media file through email, or by an email application when the user tries to send an email message.

## Prerequisites

To enable your application to use the email functionality, follow the steps below:

1.  To use the `Tizen.Messaging.Email` namespace, the application has to request permission by adding the following privilege to the `tizen-manifest.xml` file:

    ```XML
    <privileges>
       <privilege>http://tizen.org/privilege/email</privilege>
    </privileges>
    ```

2.  To use the methods and properties of the `Tizen.Messaging.Email` namespace, include it in your application:

    ```csharp
    using Tizen.Messaging.Email;
    ```

<a name="sending"></a>
## Send an email

To send an email message, follow the steps below:

1.  Create the email message with an instance of the [Tizen.Messaging.Email.EmailMessage](/application/dotnet/api/TizenFX/latest/api/Tizen.Messaging.Email.EmailMessage.html) class, and set the message subject:

    ```csharp
    var email = new EmailMessage();
    email.Subject = "CSAPI_SUBJECT";
    ```

2.  Create a recipient with an instance of the [Tizen.Messaging.Email.EmailRecipient](/application/dotnet/api/TizenFX/latest/api/Tizen.Messaging.Email.EmailRecipient.html) class, set the recipient address, and add the recipient to the message:

    ```csharp
    var recipient = new EmailRecipient();
    string address = "example@mail.com";
    recipient.Address = address;
    email.To.Add(recipient);
    ```

3.  Create an attachment with an instance of the [Tizen.Messaging.Email.EmailAttachment](/application/dotnet/api/TizenFX/latest/api/Tizen.Messaging.Email.EmailAttachment.html) class, set the attachment path, and add the attachment to the message:

    ```csharp
    var attachment = new EmailAttachment();
    string filepath = "CSAPI_FILEPATH";
    attachment.FilePath = filepath;
    email.Attachments.Add(attachment);
    ```

4.  Send the email with the `SendAsync()` method of the [Tizen.Messaging.Email.EmailSender](/application/dotnet/api/TizenFX/latest/api/Tizen.Messaging.Email.EmailSender.html) class:

    ```csharp
    var result = await EmailSender.SendAsync(email);
    ```

## Related information
* Dependencies
  -   Tizen 4.0 and Higher
