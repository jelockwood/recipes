# recipes
Autopkg recipies

These are my personal [AutoPkg](https://github.com/autopkg/autopkg) recipes. If you find any of them not working for you then raise an issue above and I will dependent on having time available see if I can fix it.

They are written in PLIST format so as to also be compatible with [AutoPkgr](https://github.com/lindegroup/autopkgr) the GUI frontend to AutoPkg. AutoPkgr does not currently accept YAML format recipes. For those unaware AutoPkg recipes operate in a chain with one recipe calling a parent recipe and that recipe in turn potentially calling another parent recipe. Therefore a typical chain might be as follows.

Download recipe (called by) <- [Munki](https://www.munki.org/munki/) recipe (called by) <- Override recipe

Note: I have found that even if you make your own override recipe in PLIST format you cannot via AutoPkgr add this to the list of overrides unless as per the above example there is a Munki recipe in PLIST format. However again using the above example you could have the Munki recipe in PLIST format and have that call a parent Download recipe in YAML format and AutoPkgr will work for this although it will show a warning symbol as it itself will not see the Download recipe as being available. Since AutoPkgr is at that point telling AutoPkg to run the Munki recipe and AutoPkg itself does support both PLIST and YAML then AutoPkg takes the info from the Munki recipe and AutoPkg successfully finds the Download recipe even if in YAML format.

This is one of the reasons I still choose to write my recipes in PLIST format and why in one or two cases I have also written my own Munki recipies in PLIST format even though a recipe in YAML already existed for the same application.

Note: There is at least one [free online tool](https://wtools.io/convert-yaml-to-plist) to translate YAML to PLIST format or vice versa, it is not always 100% correct but I did find it helpful.

I have also where needed provided versions of my recipes to download the separate Intel and Apple Silicon versions of installers for applications. This is where the author of those applications has regrettably failed to provide a universal binary version containing both. (BAD developers!)

In the case of my Azul Zulu recipies, I provide both versions written to download specific Java JDK versions and for both Intel and Apple Silicon since they are not universal binaries. (Not being universal binaries makes more sense in this case.) In theory you could use the Munki recipe the original Azul Zulu recipe author who wrote the Download recipe my Munki recipes call but he wrote them in YAML format and as I explained this means it does not work with AutoPkgr. Also in theory I could like him have written just a single Munki recipe which downloads just a specific single version of the JDK and then like him write multiple override recipes to 'override' which version to download. However then so would everyone else using my recipe. I have therefore created specific individual Munki recipes to make your life easier. I have chosen to create recipes for Azul Zulu JDK because there are more different versions available in both Intel and Apple Silicon versions than equivalent JDKs made available by other developers e.g. AWS, Microsoft and Adopt all offer fewer choices.
