# New-BurntToastNotification

## SYNOPSIS

Creates and displays a Toast Notification.

## SYNTAX

### Sound (Default)

```powershell
New-BurntToastNotification [-Text <String[]>] [-AppLogo <String>] [-Sound <String>] [-Header <ToastHeader>] [-ProgressBar <AdaptiveProgressBar>]
```

### Silent

```powershell
New-BurntToastNotification [-Text <String[]>] [-AppLogo <String>] [-Silent] [-Header <ToastHeader>] [-ProgressBar <AdaptiveProgressBar>]
```

### Snooze and Dismiss

```powershell
New-BurntToastNotification [-Text <String[]>] [-AppLogo <String>] -SnoozeAndDismiss [-Header <ToastHeader>] [-ProgressBar <AdaptiveProgressBar>]
```

### Custom Buttons

```powershell
New-BurntToastNotification [-Text <String[]>] [-AppLogo <String>] -Button <IToastButton[]> [-Header <ToastHeader>] [-ProgressBar <AdaptiveProgressBar>]
```

### Silent and Snooze and Dismiss

```powershell
New-BurntToastNotification [-Text <String[]>] [-AppLogo <String>] [-Silent] -SnoozeAndDismiss [-Header <ToastHeader>] [-ProgressBar <AdaptiveProgressBar>]
```

### Silent and Custom Buttons

```powershell
New-BurntToastNotification [-Text <String[]>] [-AppLogo <String>] [-Silent] -Button <IToastButton[]> [-Header <ToastHeader>] [-ProgressBar <AdaptiveProgressBar>]
```

### Sound and Snooze and Dismiss

```powershell
New-BurntToastNotification [-Text <String[]>] [-AppLogo <String>] [-Sound <String>] -SnoozeAndDismiss [-Header <ToastHeader>] [-ProgressBar <AdaptiveProgressBar>]
```

### Sound and Custom Buttons

```powershell
New-BurntToastNotification [-Text <String[]>] [-AppLogo <String>] [-Sound <String>] -Button <IToastButton[]> [-Header <ToastHeader>] [-ProgressBar <AdaptiveProgressBar>]
```

## DESCRIPTION

The New-BurntToastNotification function creates and displays a Toast Notification on Microsoft Windows 10.

You can specify the text and/or image displayed as well as selecting the sound that is played when the Toast Notification is displayed.

You can optionally call the New-BurntToastNotification function with the Toast alias.

## EXAMPLES

### -------------------------- EXAMPLE 1 --------------------------

```powershell
New-BurntToastNotification
```

This command creates and displays a Toast Notification with all default values.

### -------------------------- EXAMPLE 2 --------------------------

```powershell
New-BurntToastNotification -Text 'Example Script', 'The example script has run successfully.'
```

This command creates and displays a Toast Notification with customized title and display text.

### -------------------------- EXAMPLE 3 --------------------------

```powershell
New-BurntToastNotification -Text 'WAKE UP!' -Sound 'Alarm2'
```

This command creates and displays a Toast Notification which plays a looping alarm sound and lasts longer than a default Toast.

### -------------------------- EXAMPLE 4 --------------------------

```powershell
$BlogButton = New-BTButton -Content 'Open Blog' -Arguments 'https://king.geek.nz'
New-BurntToastNotification -Text 'New Blog Post!' -Button $BlogButton
```

This example creates a Toast Notification with a button which will open a link to ["https://king.geek.nz"](https://king.geek.nz) when clicked.

### -------------------------- EXAMPLE 5 --------------------------

```powershell
$ToastHeader = New-BTHeader -Id '001' -Title 'Stack Overflow Questions'
New-BurntToastNotification -Text 'New Stack Overflow Question!', 'More details!' -Header $ToastHeader
```

This example creates a Toast Notification which will be displayed under the header 'Stack Overflow Questions.'

### -------------------------- EXAMPLE 6 --------------------------

```powershell
$Progress = New-BTProgressBar -Status 'Copying files' -Value 0.2
New-BurntToastNotification -Text 'File copy script running', 'More details!' -ProgressBar $Progress
```

This example creates a Toast Notification which will include a progress bar.

### -------------------------- EXAMPLE 7 --------------------------

```powershell
New-BurntToastNotification -Text 'Professional Content', 'And gr8 spelling' -UniqueIdentifier 'Toast001'
New-BurntToastNotification -Text 'Professional Content', 'And great spelling' -UniqueIdentifier 'Toast001'
```

This example will show a toast with a spelling error, which is replaced by a second toast because they both shared a unique identifier.

## PARAMETERS

### -AppLogo

Specifies the path to an image that will override the default image displayed with a Toast Notification.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Button

Allows up to five buttons to be added to the bottom of the Toast Notification. These buttons should be created using the New-BTButton function.

```yaml
Type: IToastButton[]
Parameter Sets: Custom Buttons, Silent and Custom Buttons, Sound and Custom Buttons
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header

Specify the Toast Header object created using the New-BTHeader function, for seperation/categorization of toasts from the same AppId.

```yaml
Type: ToastHeader
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProgressBar

Specify the Progress Bar object created using the New-BTProgressBar function.

```yaml
Type: AdaptiveProgressBar
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Silent

Indicates that the Toast Notification will be displayed on screen without an accompanying sound.

Cannot be used in conjunction with the 'Sound' parameter.

```yaml
Type: SwitchParameter
Parameter Sets: Silent, Silent and Snooze and Dismiss, Silent and Custom Buttons
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SnoozeAndDismiss

Adds a default selection box and snooze/dismiss buttons to the bottom of the Toast Notification.

```yaml
Type: SwitchParameter
Parameter Sets: Snooze and Dismiss, Silent and Snooze and Dismiss, Sound and Snooze and Dismiss
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sound

Selects the sound to accompany the Toast Notification. Any 'Alarm' or 'Call' tones will automatically loop and extent the amount of time that a Toast is displayed on screen.

Cannot be used in conjunction with the 'Silent' switch.

Valid values:

- 'Default'
- 'IM'
- 'Mail'
- 'Reminder'
- 'SMS'
- 'Alarm'
- 'Alarm2'
- 'Alarm3'
- 'Alarm4'
- 'Alarm5'
- 'Alarm6'
- 'Alarm7'
- 'Alarm8'
- 'Alarm9'
- 'Alarm10'
- 'Call'
- 'Call2'
- 'Call3'
- 'Call4'
- 'Call5'
- 'Call6'
- 'Call7'
- 'Call8'
- 'Call9'
- 'Call10'

```yaml
Type: String
Parameter Sets: Sound
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

```yaml
Type: String
Parameter Sets: Sound and Snooze and Dismiss, Sound and Custom Buttons
Aliases:

Required: True
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Text

Specifies the text to show on the Toast Notification. Up to three strings can be displayed, the first of which will be embolden as a title.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default Notification
Accept pipeline input: False
Accept wildcard characters: False
```

### -UniqueIdentifier

A string that uniquely identifies a toast notification. Submitting a new toast with the same identifier as a previous toast will replace the previous toast.

This is useful when updating the progress of a process, using a progress bar, or otherwise correcting/updating the information on a toast.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value:
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

TODO

You cannot pipe input to this function.

## OUTPUTS

TODO

New-BurntToastNotification displays the Toast Notification that is created.

## NOTES

I'm *really* sorry about the number of Parameter Sets. The best explanation is:

* You cannot specify a sound and mark the toast as silent at the same time.
* You cannot specify SnoozeAndDismiss and custom buttons at the same time.

## RELATED LINKS

[New-BurntToastNotification](https://github.com/Windos/BurntToast/blob/main/Help/New-BurntToastNotification.md)
