# Azul Zulu Java Recipes for AutoPkg

### David Pirie has written AutoPkg recipes to allow downloading various releases of Azul Zulu Java. You can specify in your override recipe whether you want an Intel or Apple Silicon aka. ARM release, whether you want a JDK or JRE and which major version.

However David's recipes are provided in YAML format. These work perfectly in the command line AutoPkg tool but do not work in the GUI AutoPkgr tool.

AutoPkgr still sadly only supports plist format recipes.

As per this issue -

[https://github.com/lindegroup/autopkgr/issues/672](https://github.com/lindegroup/autopkgr/issues/672)

You can see David's recipes here -

[https://github.com/autopkg/davidbpirie-recipes/tree/main/AzulZuluJava](https://github.com/autopkg/davidbpirie-recipes/tree/main/AzulZuluJava)

I did sometime ago devise a workaround for this. If you have an AutoPkg recipe written as a plist which calls i.e. has defined as its parent recipe a YAML recipe then AutoPkgr will see the plist recipe and you can create an override of that in AutoPkgr. AutoPkgr will then run the override which will call the parent plist recipe which in turn will call the parent YAML recipe.

Therefore I have created a stripped down plist recipe which calls as its parent recipe David's YAML Munki recipe. I can then in AutoPkgr create multiple overrides all pointing to my plist - one for each Azul Zulu Java release.

Note: The recipes from David only support DMG downloads in this case and some Azul Zulu Java releases are not provided in a DMG format e.g. JRE8 for Intel.

You can see the available Azul Zulu Java releases here -

[https://www.azul.com/downloads/?package=jdk#zulu](https://www.azul.com/downloads/?package=jdk#zulu)
