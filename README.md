Munin-iptables-plugin
=====================

Zeichnet Graphen mit den Anzahl hinterlegter Regeln für jede chain.

General
-------
This was one of my first plugins.   
The behaviour is really simple: It draws for every chain a graph on the basis of the amount of rules stored in it.   
Simple, huh?   
   
The sense behind that? Well, I don't really have one but I think that somebody will need this for any kind of stuff in the future.   
   
Installation
------------
   
There are three steps required (cause the script has to be run with root privileges):   

# Adding and linkin the script correctly
First of all store the script onto the node. This can be done by cloning this repository or copy the script from the browser into your clipboard.   
Once the script is stored you have to move it to the right place. The normal (and correct) directory is unter /usr/share/munin/plugins/ .   
   
The script should belong to the user and group root and the permissions of 0755. You can orientate on the other scripts stored in the directory.   
   
# Link it
I don't know why it was made this way but it's the convention and I belive it has a deeper sense. Now we have to create a link to the script we stored in the step above.   
The command is simple: ln -s /usr/share/munin/plugins/iptables_rulescount /etc/munin/plugins/   
   
That's it. Now the last step which is one of the most important step!   
   
# Give root privileges to the script
For this step open the folling file on the node and open it with your favorite editor.   
Scroll to the end and insert this piece of code:   
   
[iptables_rulescount]   
user root   
group root   
   
# Last but not least: Restart the node
Restart the node with the command: service munin-node restart   
   
Ready. After one or two cycles of munin you should see some graphes.

Troubleshooting
---------------
Three steps:
* Has the file the right permissions
* Is the file in the right directory and is the link accessable
* Have you restarted the node

If everything fails: Contact me.
