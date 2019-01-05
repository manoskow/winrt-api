---
-api-id: E:Windows.UI.Notifications.ToastNotification.Activated
-api-type: winrt event
-api-device-family-note: xbox
---

<!-- Event syntax
public event Windows.Foundation.TypedEventHandler Activated<Windows.UI.Notifications.ToastNotification,  object>
-->

# Windows.UI.Notifications.ToastNotification.Activated

## -description
Occurs when user activates a toast notification through a click or touch. Apps that are running subscribe to this event and can receive the 

## -remarks
In the case of toast raised by a desktop app, that app must subscribe to at least the Activated event so that it can handle the expected activation of the app from the toast when the user selects it.

## -examples
The following shows an example of:
* Subscribing to the event
* Pasting the user input from selections and text boxes within the toast

```C#
//create the toast with a text input
        XmlDocument document = new XmlDocument();
        string text = "<toast launch=\"action=viewEvent&amp;eventId=63851\">" +
            "<visual>" +
            "<binding template=\"ToastGeneric\">" +
            "<text>Thank you for using our helpdesk.</text>" +
            "<text>Do you have our </text>" +
            "</binding>" +
            "</visual>" +
            "<actions>" +
            "<input id=\"textBox\" type=\"text\" placeHolderContent=\"Enter Text\">" +
            "</input>" +
            "<action hint-inputId=\”textBox\” activationType=\"system\"arguments=\
            "action=rsvpEvent&amp;eventId=63851\" content=\"Send\"/>" +
            "</actions>" +
            "</toast>";
 
        document.LoadXml(text);
        ToastNotification notification = new ToastNotification(document);
 
        //add the event 
        notification.Activated += Notification_Activated;
        notifier.Show(notification);
        notificationList.Add(notification);

      . . . . .

//retrieve the user input from the toast activated arguments
private void Notification_Activated(ToastNotification sender, object args)
{
        ToastActivatedEventArgs activatedArgs = (ToastActivatedEventArgs)args;
 
        // Retrieve the arguments
        string arguments = activatedArgs.Arguments;
 
        // Retrieve the text input
        string textInput = activatedArgs.UserInput["textBox"];

        PerformSelectionAction(arguments, textInput);
        
}

```

## -see-also
[Toast notifications sample](http://go.microsoft.com/fwlink/p/?linkid=231503), [Sending toast notifications from desktop apps sample](http://go.microsoft.com/fwlink/p/?linkid=231503), [Toast XML schema](https://docs.microsoft.com/uwp/schemas/tiles/toastschema/schema-root), [Tiles, badges, and notifications](http://msdn.microsoft.com/library/48ee4328-7999-40c2-9354-7ea7d488c538), [Quickstart: Sending a toast notification](http://msdn.microsoft.com/library/098df37c-4d40-4499-b809-ccb651da1cba), [Quickstart: Sending a toast push notification](http://msdn.microsoft.com/library/bb962e30-6c95-4186-8a0e-6683140e17c7), [Quickstart: Sending a toast notification from the desktop](http://msdn.microsoft.com/library/1d20ed75-e24a-4e60-91ab-cfcbe902a68e), [Guidelines and checklist for toast notifications](http://msdn.microsoft.com/library/002951e3-3d2d-454a-a0b7-daa5c1e7178a), [How to handle activation from a toast notification](http://msdn.microsoft.com/library/74ba3513-0a52-46a0-8769-ed58abe7c05a), [How to opt in for toast notifications](http://msdn.microsoft.com/library/809cdd36-6de1-4de0-88b2-62b46cafdb28), [How to schedule a toast notification](http://msdn.microsoft.com/library/18a09413-1679-4606-8175-346f4fe6a4f8), [How to enable desktop toast notifications through an AppUserModelID](http://msdn.microsoft.com/library/bb32cd0a-99e6-47dc-a913-39a7b3027314), [The toast template catalog](http://msdn.microsoft.com/library/1a437614-4259-426b-8e3f-ca57368b2e7a), [Toast audio options](http://msdn.microsoft.com/library/12185879-1f9b-4bdc-99e7-a6f2f62806cb)
