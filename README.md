flickr-uploader
===============

Upload a directory of media to Flickr to use as a backup to your local storage.

## Features:
* Uploads images in full resolution to Flickr account (JPG, PNG...)
* Reuploads modified images
* Removes images from Flickr when they are removed from your local hard drive
* Uploads videos (AVI, MOV, MPG, MP4, 3GP...)
* Stores image information locally using a simple SQLite database
* Creates "Sets" based on the folder name the media is in (getting existing sets from Flickr is managed also)
* Ignores unwanted directories (like ".picasabackup" for Picasa users)
* Convert RAW files (with an external tool)

THIS SCRIPT IS PROVIDED WITH NO WARRANTY WHATSOEVER. PLEASE REVIEW THE SOURCE CODE TO MAKE SURE IT WILL WORK FOR YOUR NEEDS. IF YOU FIND A BUG, PLEASE REPORT IT.

## Requirements:

* Python 2.7+
* File write access (for the token and local database)
* Flickr API key (free)

## Setup:
Go to http://www.flickr.com/services/apps/create/apply and apply for an API key
Edit the following variables in the uploadr.ini:


* FILES_DIR = "YourDir"
* FLICKR = {
        "title"                 : "",
        "description"           : "",
        "tags"                  : "auto-upload",
        "is_public"             : "0",
        "is_friend"             : "0",
        "is_family"             : "0",
        "api_key"               : "Yourkey",
        "secret"                : "YourSecret"
        }
* FLICKR["api_key"] = ""
* FLICKR["secret"] = ""

## Usage
Place the file uploadr.py in any directory and run (execution privs required):

$ ./uploadr.py

It will crawl through all the files from the FILES_DIR directory and begin the upload process.

## Q&A
* Q: Who is this script designed for?
* A: Those people comfortable with the command line that want to backup their media on Flickr in full resolution.

* Q: Why don't you use OAuth?
* A: The older method is simpler to understand and works just as good. No need to fix what isn't broken.

* Q: Are you a python ninja?
* A: No, sorry. I just picked up the language to write this script because python can easily be installed on a Synology Diskstation.

* Q: Is this script feature complete and fully tested?
* A: Nope. It's a work in progress. I've tested it as needed for my needs, but it's possible to build additional features by contributing to the script.

* Q: How to automate it with a Synology NAS ?
* A: With DSM 5, create an automate task, make it run once a day for example, and put this in the textbox without quotes "/usr/local/python/bin/python path_to_your_script"
for ie, "/usr/local/python/bin/python /volume1/script/flickr-uploader/uploadr.py"
