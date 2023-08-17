IBM Notifier (SUPER)
=========

IBM Notifier is an app written by IBM's internal support team and allows scripts to use it to display dialogs complete with fields, progress bars, etc.

It is normally installed in the the /Applications/ directory and there are existing AutoPkg recipes to download and update IBM Notifier in this location as written by Alex Narvey aka @precursoca. However another open source project called S.U.P.E.R. downloads and installs a copy in to a non-standard location in /Library/Management/super/

These recipes therefore have been written specifically to update a copy of IBM Notifier in that location. This is done by first using an AutoPkg pkg recipe which takes the downloaded dmg produced by the download recipe from precursoca
