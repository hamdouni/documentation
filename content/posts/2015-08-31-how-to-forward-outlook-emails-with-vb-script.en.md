---
title: 'How To Forward Outlook Emails With VB Script [EN]'
author: Brahim
type: post
date: 2015-08-31T05:30:05+00:00
url: /how-to-forward-outlook-emails-with-vb-script/
wp-to-buffer-success:
  - 1
categories:
  - How to ?
tags:
  - outlook
  - windows

---
  1. In Windows, create a certificate via Start > All Programs > Microsoft Office > Microsoft Office Tools > Digital Certificate for VBA Projects
  2. In Microsoft Outlook, open the VB editor and copy/paste the code below
  3. Replace **your@email.here** and save
  4. Click on Tools > Digital Signature
  5. Click on [Choose] and select your certificate
  6. Click OK, then save and close the VB editor
  7. Create the Outlook rule with [run a script] as action and select your macro
  8. That&#8217;s all folks !

    Private Const TO_EMAIL As String = "your@email.here"
    Sub ForwardAllEmail(theMail As MailItem)
    	On Error GoTo EndSub
    	Dim mailObj As Outlook.MailItem
    	Dim item As Outlook.MailItem
    	Set mailObj = Application.Session.GetItemFromID(theMail.EntryID)
    	Set item = mailObj.Forward
    	item.Recipients.Add (TO_EMAIL)
    	item.Send
    	Set item = Nothing      ' Set variables to null to prevent memory leaks
    	Set mailObj = Nothing
    	Exit Sub
    EndSub:
      MsgBox "Error: " & Err.Description
    End Sub