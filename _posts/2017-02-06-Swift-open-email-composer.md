---
layout: post
title:  "Swift open email composer"
date:   2017-02-06 11:00:00
categories: CodeSnippet
tags: IBAction email MessageUI MFMailComposeViewController canSendMail
---

Following is code snippet for opening email composer.

```swift
import MessageUI

@IBAction func btnOpenEmail(_ sender: AnyObject) {
    self.sendEmail()
}

func sendEmail() {
    if MFMailComposeViewController.canSendMail() {
        let mail = MFMailComposeViewController()
        mail.mailComposeDelegate = self
        mail.setToRecipients([self.lblEmail.text!.trimmingCharacters(in: CharacterSet.whitespaces)])
        present(mail, animated: true)
    } else {
        // show failure alert
    }
}

func mailComposeController(_ controller: MFMailComposeViewController, didFinishWith result: MFMailComposeResult, error: Error?) {
    controller.dismiss(animated: true)
}
```
