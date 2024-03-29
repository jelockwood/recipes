IBM Notifier (SUPER)
=========

[UPDATE - I have since discovered that version 3.0 of the SUPER script deliberately installs an older version of IBM Notifier, version 2.9.1. It also when it does a normal automated run checks to see if the copy has changed or is missing and therefore also will replace any newer version with the same 2.9.1. Therefore currently there is no point using this recipe. If this behaviour changes I will update this README but clearly until then there is no point using this recipe.
]

[IBM Notifier](https://github.com/IBM/mac-ibm-notifications) is an app written by IBM's internal support team and allows scripts to use it to display dialogs complete with fields, progress bars, etc.

It is normally installed in the the /Applications/ directory and there are [existing AutoPkg recipes](https://github.com/autopkg/precursorca-recipes/tree/master/IMB.Notifier) to download and update IBM Notifier in this location as written by Alex Narvey aka @precursoca. However another open source project called [S.U.P.E.R.](https://github.com/Macjutsu/super) downloads and installs a copy in to a non-standard location in /Library/Management/super/

These recipes therefore have been written specifically to update a copy of IBM Notifier in that location. This is done by first using an AutoPkg pkg recipe which takes the downloaded dmg produced by the download recipe from precursoca and builds a custom installer pkg. This custom installer pkg then rather than merely copying the app to the standard /Applications/ directory instead copies it to the /Library/Management/super/ location, it also checks that a copy already exists in that location and if not exits without doing anything.

Note: When the S.U.P.E.R. script is installed it as mentioned downloads and installs its own copy of IBM Notifier in to its own location. I have therefore written these recipes so they only do an install/update if there is already a copy in that location as unless S.U.P.E.R. has been successfully installed there is no point doing this. Admins should therefore not use this with Munki as a managed or optional installer but only as a managed update.
