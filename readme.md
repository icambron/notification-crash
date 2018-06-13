# Notification crash

This add-in is a minimal reproduction of a Outlook bug that causes OWA to be unusable until reloaded.

## Install

These files are pushed to gh-pages, so you can install it directly from here:

https://isaaccambron.com/notification-crash/manifest.xml

## Steps to reproduce

 1. Open Outlook in your favorite browser (I used Chrome)
 1. Turn on notifications for new emails
 1. Compose a new message
 1. Click the add-in's button (it's the S-looking thing)
 1. A task pane will slide out, and it will immediately open a dialog
 1. Leave the dialog open
 1. Send yourself an email from another client
 1. Wait until the notifications shows up behind the scrim (or you see the email itself show up)
 1. Try to close the dialog.
 1. Nothing happens
 1. Note the stack trace in the developer console

## Notes
 * It seems to be possible to avoid this issue by not using the iframed modal, but that's a subtantially worse user experience
 * We'd of course love for notifications not to kill our task pane at all, and not only because it's the likely root cause of this issue.
 * I'm able to reproduce this consistently with this test add-in, but a couple of colleagues reported that it doesn't always for them, presumably because in some cases the notification doesn't always close the task pane at all (and thus doesn't strand the modal).
