SHELL := /bin/bash

1PASSWORD_ICLOUD_PASSWORD := $(shell op get item "iCloud mailsync app password" | jq '.details.fields[] | select(.designation=="password").value')
1PASSWORD_ICLOUD_USERNAME := $(shell op get item "iCloud mailsync app password" | jq '.details.fields[] | select(.designation=="username").value')

1PASSWORD_TRANSIP_PASSWORD := $(shell op get item "TransIP Webmail" | jq '.details.fields[] | select(.designation=="password").value')
1PASSWORD_TRANSIP_USERNAME := $(shell op get item "TransIP Webmail" | jq '.details.fields[] | select(.designation=="username").value')

imapsync:
	@imapsync \
		--host1 imap.mail.me.com --user1 ${1PASSWORD_ICLOUD_USERNAME} --password1 ${1PASSWORD_ICLOUD_PASSWORD} \
		--host2 imap.transip.email --user2 ${1PASSWORD_TRANSIP_USERNAME} --password2 ${1PASSWORD_TRANSIP_PASSWORD} \
		--dry --folderrec Gegevens --folderrec gmail --folderrec Text --folderrec webfaction