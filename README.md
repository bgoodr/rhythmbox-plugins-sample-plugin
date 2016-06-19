# rhythmbox-plugins-sample-plugin
Rhythmbox sample plugin

## Sample python plugin

Here is what I did to create this plugin:

Read most of the web page at:

https://wiki.gnome.org/Apps/Rhythmbox/Plugins/WritingGuide

Download the source for Rhythmbox 3.3 and copied the plugin source here

cp -rp rhythmbox-3.3/sample-plugins/sample-python/ .

Remove sample-python/Makefile.am and check that in:

    git rm -f sample-python/Makefile.am 

Rename the .in file to have the correct extension:

    git mv sample-python/sample-python.plugin.in sample-python/sample-python.plugin

Remove the "_" in front of the keys inside the sample-python/sample-python.plugin file:

    _Name=Python Sample Plugin
    _Description=A sample plugin in Python with no features

Copy the
https://github.com/donaghhorgan/rhythmbox-plugins-open-containing-folder/blob/master/install.sh
file into sample-python/

    curl https://raw.githubusercontent.com/donaghhorgan/rhythmbox-plugins-open-containing-folder/master/install.sh > sample-python/install.sh
    chmod a+x sample-python/install.sh
    git add sample-python/install.sh

Modify install.sh to generalize it for use in future python plugins
(the install.sh had hardcoded names in it).

Execute rhythmbox with debug filter to see the print statements (see why at https://wiki.gnome.org/Apps/Rhythmbox/Plugins/WritingGuide#Activation):

    rhythmbox -D "sample python"

But notice that they still do not show up. You have to enable the
plugin under Tools/Plugins menu, click the checkbox. I found I had to
click the checkbox multiple times before I started seeing output on
the console:

    brentg@wilddog:~/bgoodr/rhythmbox-plugins-sample-plugin/sample-python$ rhythmbox -D "sample"
    (09:58:41) [0x182a2c0] [SamplePython.do_activate] /home/brentg/.local/share/rhythmbox/plugins/sample-python/sample-python.py:29: activating sample python plugin
    
    (rhythmbox:11782): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist
    
    
    (rhythmbox:11782): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist
    
    
    (rhythmbox:11782): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist
    
    
    (rhythmbox:11782): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist
    
    
    (rhythmbox:11782): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist
    
    
    (rhythmbox:11782): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist
    
    (09:58:49) [0x182a2c0] [SamplePython.do_deactivate] /home/brentg/.local/share/rhythmbox/plugins/sample-python/sample-python.py:51: deactivating sample python plugin
    /home/brentg/.local/share/rhythmbox/plugins/sample-python/sample-python.py:27: Warning: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
      self.source.delete_thyself()
    (09:58:59) [0x182a2c0] [SamplePython.do_activate] /home/brentg/.local/share/rhythmbox/plugins/sample-python/sample-python.py:29: activating sample python plugin

Notice that on the left side panel we see "Python Source"
entry. Clicking on that shows nothing which I am guessing is to be
expected for this sample plugin.

