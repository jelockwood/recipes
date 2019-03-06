# recipes
Autopkg recipies

These are my personal AutoPkg recipes.

The Draw.io one replaces the currently broken one at - https://github.com/autopkg/peshay-recipes/tree/master/drawio it lacks a valid munki recipe.

The Rocket.Chat desktop client is a new one since there was no existing one I could find.

The Gifox one is for the GIF tool, there seems to only be a partial one of this for JSS, mine is a full one for Munki. 

The libmacgpg-free one downloads a replacement library for GPGSuite and then wraps it in an installer package to restore 'free' functionality to the GPGSuite, you need to use the existing GPGSuite recipe to download that and then this recipe to download the replacement library/plugin.

This Notion recipe replaces an existing one. The existing one scrapes a JSON file which has not been updated for a long time and hence it does not find current updates. My replacement uses an alternative method and finds the current version.

NordVPN is a commercial VPN service, this is a new recipe to download the latest Mac client.

Smartmontools is a command line tool to query the SMART status of drives fitted to your Mac. Amongst other things this tool is used by MunkiReports.

Pinpoint is a command line tool to obtain the location of a Mac. It uses GoogleAPIs to do this as Apple now block automated access to their 'location service'. It is used by MunkiReport for reporting location information. See - https://github.com/jelockwood/pinpoint
