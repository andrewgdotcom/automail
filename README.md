# Automail

Automail is a utility to allow a user with no shell access to manipulate his procmail settings by sending specially formatted emails to himself. It consists of a perl script and several procmail template files which are include-ed by his ~/.procmailrc file. To initialise the system, the automail template must be include-ed by hand or by placing the included .procmailrc file in /etc/skel . The syntax is:

	include /var/local/procmail-templates/automail

Once this is done, the user sends himself an email with the subject line "automail! help" and instructions are sent to him via a return email. All communication between automail and the user takes place via email dialogue in a style similar to mailman.


## Usage

	Automail reads your Subject: and manages your email settings accordingly.

	Syntax:
    		automail! [command]
	(the exclamation mark is significant!) where command is one of:

	help
  		prints this message
	status
  		prints the status of the automail management system
	[un]set vacation [vacation subject line]
  		sets a 'vacation' message telling the world that you're on holiday.
  		The rest of the subject line is taken as the subject of the vacation
  		email, and the body of the mail is reproduced as the vacation message.
	[un]set forward [forwarding address]
  		sets your forwarding address to the address specified. Copies of your
  		emails will still be delivered to your local mailbox. 
	[un]set spamfilter
  		controls whether your email will be filtered for spam. When active,
  		suspected spam will be moved to a subfolder 'spam' of your inbox.
	disable yourself completely
  		disables automail so that it can only be turned back on again by
  		manually editing the procmailrc file on the mail server.

	Examples:

        	Subject: automail! status

        	Subject: automail! set forward foo@bar.com

        	Subject: automail! set vacation I am away on holiday until 22nd
            	(message body contains email reply to be sent)

        	Subject: automail! unset vacation

        	Subject: automail! disable yourself completely

