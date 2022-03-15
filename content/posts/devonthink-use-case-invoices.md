---
title: "Devonthink Use Case: Invoice Management"
date: 2022-03-15T19:05:45+01:00
draft: false
---

For several years, [DEVONthink](https://www.devontechnologies.com/apps/devonthink) has gradually found its way into my app stack. Initially, I think I struggled a little with what to store in it, how to organize my databases, and so on. When I started thinking about it as a file manager and a way to organize pretty much all my files, things started to become easier and I started building some workflows on top of the base functionality. One of those use cases is how I manage invoices and that is what I want to describe in this post.

Even though most of my paperwork is digital these days, not everything goes directly into the bank and can be easily approved for payment. I pay all my invoices monthly, at the end of the month. When that time comes, I need to gather the invoices I need to pay from primarily three different sources:

1. The ones that are sent electronically, directly to my bank. These I pretty much only need to approve and they are done.
2. The ones that are sent electronically, but as PDFs via e-mail or personal digital inbox[^1]. With these, I typically open them on the screen and use the mobile bank app on my phone to scan the details required (destination, reference number, and invoice amount).
3. Paper invoices sent as letters through the old-school mail. For these, I apply the same process as with number 2 above, but for me to be able to do it from anywhere (without physical access to these documents) I scan them as PDF files.

[^1]: In Sweden, like many other countries I imagine, we have a system of personal digital inboxes where digital post such as invoices, tax papers, statements, etc can be received.

Given this information, I have a shortlist of requirements that my invoice management solution must fulfill:

- Easy capture of PDF files (I need to gather the files from categories 2 & 3) for both myself and my wife.
- Easy to scan paper invoices to PDF format (specifically for category 3)
- Organized by the month I receive them so that I can easily find the invoices for a given month
- Keeping a status: is the invoice paid or not?
	- If it is paid already, it should be marked and the date of payment should be recorded

Until I implemented the [DEVONthink](https://www.devontechnologies.com/apps/devonthink) workflow I'm about to describe I have used various manual or semi-automatic solutions such as: just keeping a file of unpaid invoices in my home office; scanning and tagging in Evernote; a Dropbox folder. It never worked very well and there were several manual and sometimes cumbersome steps.

## The Workflow

To solve the two first requirements with one app, I decided to go for a shared [Dropbox](https://www.dropbox.com) folder to gather the incoming invoices. Both I and my wife have free, personal Dropbox accounts that we use for smaller projects like this. In addition, Dropbox has a pretty good document scanner feature built-in. With this shared folder in place, we can both just drop the invoice files in and they are out of sight, out of mind. 

The next thing to tackle was how to get the files from the `Incoming invoices` folder into DEVONthink, and organized by month. Initially, I thought of using [Folder Actions](https://www.devontechnologies.com/blog/tipusefolderactions), but even though solving the problem for me, I found that handling it inside DEVONthink with [Smart Rules](https://www.devontechnologies.com/blog/20201110-organize-with-smart-rules) was a more flexible solution for me. I created a group called Invoices and inside this group, I added the `Incoming invoices` as an indexed folder:

![](/dt/folder-structure.png#center)

Then I created the `Import Invoice` smart rule with the following configuration:

![](/dt/import-invoice-rule.png#center)

Essentially, when DEVONthink finds a PDF file in the `Incoming Invoices` folder, it will:

- Move the PDF from the Dropbox folder into my database
- Add the tag `UnpaidInvoice`
- Imprint the PDF with a stamp (see further down for details)
- Move the PDF to the Invoices group
- File it into a sub-group with the format Year-Date (based on the file creation date); and lastly
- Show a notification that the file was imported

With this in place, when it's time for me to pay the monthly invoices, I can go to one place and have all the invoices neatly organized with a tag to indicate the status. After paying an invoice, I simply removed the `UnpaidInvoice` tag, and by the end of the year, I grouped all the sub-groups (Year-Date) into one group for the year.

I used this setup like this for quite a while until I realized that I didn't want to manually remove the tag after paying each invoice. Furthermore, I also realized that I didn't track the date of payment anywhere. I decided to add another Smart Rule, but this one would be activated manually (by right-clicking on a selection and choosing Apply Rules). 
It simply removes the tag and imprints the PDF with a text on the middle of the page that says 'PAID' and today's date.

![](/dt/invoices-paid-rule.png#center)


## Imprinter configurations

The following two imprinter configuration is used to add text to the PDF with information about the filename when it was imported, and a permanent link to the DEVONthink item.

![](/dt/import-imprinter.png#center)

This imprinter configuration adds a semi-transparent 'PAID' text in large red letters in the middle of the page with the date of the payment on a line below. See the second image for an example.

![](/dt/invoice-paid-imprinter.png#center)

![](/dt/invoice-imprinted.png#center)