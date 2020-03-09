#  Backblaze(B2) - Ghost Storage 

This library works with current version of Ghost 3.x.x

B2 Ghost Storage allows ghost to save images to Backblaze B2, with options of creating subfolders in their B2 buckets and if the files are saved using /Year/Month/Filename.png or just filename.png


# Installation

Via NPM
```
go to ghost installation folder
npm i b2-ghost-storage
mkdir  -p  ./content/adapters/storage
cp  -r  ./node_modules/b2-ghost-storage  ./content/adapters/storage/b2-ghost-storage
npm install
```

Via GIT
```
go to ghost installation folder
mkdir -p ./content/adapters/storage/b2-ghost-storage
cd content/adapters/storage/b2-ghost-storage
git clone https://github.com/anazhd/b2-ghost-storage.git .
npm  install

```

## Configuration

Add this in `config."GHOST_ENVIRONMENT".js` file

```
"storage": {
	"active": "b2-ghost-storage",
	"b2-ghost-storage": {
		"accountId": "MASTERKEY_ID",
		"applicationKey": "MASTER_APPLICATION_KEY",
		"bucketId": "YOUR_BUCKET_ID",
		"bucketName": "YOUR_BUCKET_NAME",
		"subFolder": "OPTIONAL_SUBFOLDER",
		"useDatedFolder": true, //true or false
		"host": "http://<your_backblaze_url>"
	}
}
```

If you don't have an account, you can create your account [here](https://www.backblaze.com) and then create your bucket.

## Backblaze url
Open your bucket in Backblaze, upload an image, click "i" button to see the image details. From there, check on the Friendly url section, that is your backblaze url. It varies from your settings. If you put subFolder above then the url should be with the subfolder.

e.g with subfolder
>https://f002.backblazeb2.com/file/atestbucket

e.g without subfolder
>https://f000.backblazeb2.com/file
![url](https://i.imgur.com/OiG6pjz.jpg)

You'll need this else if you upload the same image name, it will overwrite the other image with same name. Read below for info if you set this up correctly.

## ETC

By default, if you uploaded the same image name twice, for example image.jpg the second image will be renamed with number like so image-1.jpg and so on. This is how ghost iamge upload and ghost storage base default nature. Unless if the storage base is broken or you put the wrong backblaze url, then it wont work I guess (haven't fully test this as I do different stuff in my own version).
