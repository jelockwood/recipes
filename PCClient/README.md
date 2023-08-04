PCClient
============

A set of AutoPkg recipes to download the Mac PaperCut Client from a PaperCut MF server.

The Download recipe
------------

The PaperCut MF server installer when installed automatically generates a matching set of clients for Mac, Windows and Linux. This is stored in a sub-directory of the PaperCut server and the Mac client is merely a standard Mac app and not a pkg, dmg or zip. As the Mac client is effectively a directory with subfolders on the PaperCut server it cannot be downloaded using the standard URLDownloader processor as this uses CURL which does not support recursive downloads.

I have set my PaperCut server to share the subdirectory via a web server and also set the server to run an automated task to make a zip file of the Mac client. The download recipe therefore downloads this zip file. It should be possbile for other users to do the same whether they are using a Mac, Windows or Linux server.

The download recipe now relies on both the URL and the zip file name to be supplied via a users override recipe. The following is what therefore the URLDownloader section of the download recipe looks like.

~~~xml
	<key>Process</key>
	<array>
		<dict>
			<key>Arguments</key>
			<dict>
				<key>url</key>
				<string>%my_url%%my_zip%</string>
			</dict>
			<key>Processor</key>
			<string>URLDownloader</string>
		</dict>
	</array>
~~~

Note the important fact that the URLDownloader processor _does not_ insert the forward slash before the name of the zip file, you should include this at the end of your URL value in your override recipe.

If your full URL looks like this ```https://myserver.mydomain.com/myfile.zip``` then you need to put the following in your override recipe as the Input section.

~~~xml
	<key>Input</key>
	<dict>
		<key>NAME</key>
		<string>PCClient</string>
		<key>my_url</key>
		<string>https://myserver.mydomain.com/</string>
		<key>my_zip</key>
		<string>myfile.zip</string>
	</dict>
~~~

If your full URL looks like this ```https://myserver.mydomain.com/folder/folder/myfile.zip``` then you need to put the following in your override recipe as the Input section.

~~~xml
	<key>Input</key>
	<dict>
		<key>NAME</key>
		<string>PCClient</string>
		<key>my_url</key>
		<string>https://myserver.mydomain.com/folder/folder/</string>
		<key>my_zip</key>
		<string>myfile.zip</string>
	</dict>
~~~

If you fail to correctly define the above in your override recipe then the download recipe will fail.

The Pkg recipe
------------
The pkg recipe unarchives the zip file, it also creates preinstall and postinstall scripts a launchdaemon plist and then builds an installer pkg.

The Munki Recipe
------------
The munki recipe then uploads the installer pkg to a Munki repo.

(Your own) override recipe
------------
As discussed above with regards to the download recipe you need to edit your own override recipe so that the URL and zip file name will be provided to AutoPkg.

This approach has allowed me to create a set of recipes that can be easily used for all users without having to hardcode in to my own recipes the URL of the server and therefore require all users to make their own copies of these recipes and put them on their own Github repo.

I am also hoping to allow the override recipe to define the PaperCut server address to use to automatically modify the paper.properties file inside the Mac PCClient.app before the installer pkg is created. Yes, the PaperCut server is supposed to set this automatically but this gives more control if needed.

