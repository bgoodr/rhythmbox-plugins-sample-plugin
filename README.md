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

Remove the "_" in front of the keys inside the sample-python/sample-python.plugin file:

    _Name=Python Sample Plugin
    _Description=A sample plugin in Python with no features

Copy the https://github.com/donaghhorgan/rhythmbox-plugins-open-containing-folder/blob/master/install.sh file into sample-python/

    curl https://raw.githubusercontent.com/donaghhorgan/rhythmbox-plugins-open-containing-folder/master/install.sh > sample-python/install.sh
    chmod a+x sample-python/install.sh
    git add sample-python/install.sh

