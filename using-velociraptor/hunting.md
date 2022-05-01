# 🕵 Hunting

### What is a Hunt?

An analyst or investigator can collect one or more of the same artifacts across multiple clients using a <mark style="color:green;">**Hunt**</mark>.&#x20;

### Schedule a new Hunt <a href="#schedule-a-new-hunt" id="schedule-a-new-hunt"></a>

<mark style="color:green;">**Hunts**</mark> are conducted via the <mark style="color:green;">**Hunt Mananager**</mark> component which is accessible from the tab on the left side navigation table.

![Screenshot showing Hunt Manager tab](../.gitbook/assets/hunt\_manager.png)

Schedule a new hunt by clicking the plus ("+") button at the top left.

![](<../.gitbook/assets/add\_hunt (2).png>)

#### Configure the Hunt

Give the <mark style="color:green;">hunt</mark> a description and set the expiration date. The "Include Conditions" parameter is where the range of client endpoints is set. Conditions fall into three categories:

* Run everywhere
* Run by label
* Run by Operating System

For this example, a hunt was run against all Linux clients.

![Example Hunt](../.gitbook/assets/example\_hunt.png)

Note that excluded conditions can also be added. None were used in this example because it is impractical for the small scale of the network.

Under the "Exclude Condition" parameter is a display box which shows the number of clients that this <mark style="color:green;">hunt</mark> will reach. For this example it will be run against the one Linux box: lnxwks02.

#### Select Artifacts

The next step is to select the artifacts to <mark style="color:green;">hunt</mark> for. Do this by looking through the list or by using the search bar at the top.&#x20;

![](../.gitbook/assets/hunt\_monitoring.png)

#### Configure Parameters

An <mark style="color:green;">artifact</mark> added to the <mark style="color:green;">hunt</mark> after clicking on it. Check which <mark style="color:green;">artifacts</mark> are included in the "Configure Parameters" tab.

![](../.gitbook/assets/config\_params.png)

#### Review

This tab shows the raw <mark style="color:green;">VQL</mark> output of the <mark style="color:green;">hunt</mark>.

#### Launch

After setting all  desired artifacts and paramters, click the "Launch" button at the end of the options bar. This will return you to the <mark style="color:green;">Hunt Manager</mark> page. From here select the <mark style="color:green;">hunt</mark> and click the play button at the top and then "Run It" from the pop up box to begin <mark style="color:green;">hunting</mark>.&#x20;

![](../.gitbook/assets/start\_hunt.png)

![Screenshot showing Pop-Up box](../.gitbook/assets/run\_it.PNG)

A <mark style="color:green;">hunt</mark>'s progress progress at anytime and looking at the "Results" information box on the right side of the page.

![](<../.gitbook/assets/results (1).png>)

This is also where results can be downloaded as a file.

### Post-process a hunt <a href="#post-process-a-hunt" id="post-process-a-hunt"></a>

After a hunt has collect an artifact, <mark style="color:green;">Velociraptor</mark> creates a notebook for each hunt where a <mark style="color:green;">VQL</mark> query to the results can be applied.&#x20;

To view the raw notebook, click the left most icon above the display table:

![](<../.gitbook/assets/open vql 1 (1).png>)

This will open up a new menu. Click on the icon that is shaped like a pencil to open the raw notebook code:

![](<../.gitbook/assets/open vql 2 (1).png>)

Here is what the default notebook for the collected artifact "Linux.Sys.Users" looks like:

![](../.gitbook/assets/example\_linux\_host.PNG)

This can be parsed by adding to the VQL query. For example, the <mark style="color:blue;">`WHERE`</mark> sentence and adding a column name and a value from that column. In the screenshot below the following command was added to the notebook: <mark style="color:blue;">`WHERE User = "root"`</mark>&#x20;

![](../.gitbook/assets/sort\_by\_root.PNG)
