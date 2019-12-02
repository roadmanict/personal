.PHONY: clean dist deploy

SHELL := /bin/bash

HOST:=
FTP_USER:=
FTP_PASS:=
TARGETFOLDER:='/www'
SOURCEFOLDER:='./dist'

clean:
	rm -rf dist/

dist:
	mkdir -p dist/
	rsync -ahSD --ignore-errors --force --delete --stats config vendor web .htaccess dist/
	# cp -r config/ vendor/ web/ .htaccess dist/

deploy:
	lftp -d \
		-u ${FTP_USER},${FTP_PASS} \
		-e "mirror --reverse --delete --verbose --include config --include vendor --include web --include .htaccess ${SOURCEFOLDER} ${TARGETFOLDER}; quit" \
		${HOST}