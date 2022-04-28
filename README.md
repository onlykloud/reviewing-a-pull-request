## Welcome to awesome game of Tetris

A project based learning activity for people who are getting started with Git and GitHub.
You can play the game at: https://onlykloud.github.io/github-games/
To play the game:
1. Go to the **Settings** tab of this repository.
1. Scroll down to the section titled _GitHub Pages_
1. Select **main** from the Source drop-down.
1. Click **Save**.
1. Navigate to the URL provided in the same section.

### Instructions for playing the game

1. Press the space bar to begin.
2. Use the up and down arrow keys to rotate the shape.
3. Use the left and right arrow keys to position the shape.
4. The goal is to create complete rows with no empty spaces.
5. When completed, the rows will disappear.
6. To pause the game, just press the space bar again.

>> _*SUPPORTED BROWSERS*: Chrome, Firefox, Safari, Opera and IE9+_

This fun open source game was cloned from: https://github.com/jakesgordon/javascript-tetris

// Container CPU 
// View all the container CPU usage averaged over 30mins. 
// To create an alert for this query, click '+ New alert rule'
//Select the Line chart display option: can we calculate percentage?
Perf
| where ObjectName == "K8SContainer" and CounterName == "memoryRssBytes"
| extend PodUid = tostring(split(InstanceName, '/',9)[0]), Container = tostring(split(InstanceName, '/', 10)[0])
| join kind=leftouter (KubePodInventory | summarize arg_max(TimeGenerated, *) by PodUid) on PodUid
| where Namespace == "default"
| summarize Memora_RAM_Utilizada = avg(CounterValue)/100000 by format_datetime(bin(TimeGenerated, 40m),'yyyy-M-dd [H:mm:ss]') , Controller_Name = Name, Namespace
