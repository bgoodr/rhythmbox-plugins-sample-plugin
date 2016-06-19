# rhythmbox-plugins-sample-plugin
Rhythmbox sample plugin

## Sample python plugin

Here is what I did

Download the source for Rhythmbox 3.3 and copied the plugin source here

cp -rp rhythmbox-3.3/sample-plugins/sample-python/ .

Remove sample-python/Makefile.am and check that in:

    git rm -f sample-python/Makefile.am 

Rename the .in file to have the correct extension:

    git mv sample-python/sample-python.plugin.in sample-python/sample-python.plugin

