# recipes
Autopkg recipies
These are my personal AutoPkg recipes.

The Draw.io one replaces the currently broken one at - https://github.com/autopkg/peshay-recipes/tree/master/drawio it lacks a valid munki recipe.

The Rocket.Chat+ one is a new one since there was no existing one I could find.

The munki one is a version I am testing that should hopefully download the latest munkitools pkg, create a pkginfo which excludes the launchd component via the use of installer_choices_xml and receipts arrays.
