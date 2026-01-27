---
title: Home
---

<br>
<center>
<h1> Hi Alexis 👋</h1>
<p>Today is <b> <span class="date"> <% tp.date.now("dddd, MMMM Do, YYYY") %> </span> </b></p>
<p> <font size=2> This page is your central hub for navigating your digital workspace. </font></p>
</center>
<br>

___

<br>

<div class="parent-container">

<div class="left-container">

<h3> <font size=4>📓 Daily Notes</font></h3>
<br>
<div class="double-line-all">

```dataview
TABLE date as "Date"
FROM "10-19 Journal"
WHERE file.name != "Personal-Journal"
SORT file.name DESC
LIMIT 5
```
</div>

<br>

<h3> <font size=4>✅ Open Tasks</font></h3>
<br>
<div class="double-line-all">

```dataview
TASK
FROM ""
WHERE !completed
```
</div>

</div>

<div class="right-container">

<h3> <font size=4>📆 Calendar</font></h3>
<br>
<div class="double-line-all">

```calendar
```
</div>

<br>

<h3> <font size=4>🗂️ Quick Links</font></h3>
<br>
<div class="double-line-all">

- [[00-09 System/02 Inbox/Inbox|📥 Inbox]]
- [[00-09 System/01 Templates/Daily Note|📓 Daily Note Template]]
- [[10-19 Journal/Personal-Journal|👨 Personal Journal]]
</div>

</div>

</div>

<br>

<h3> <font size=4>🚀 Areas & Projects </font></h3>
<br>

<div class="parent-container-grid">
<div class="double-line-all">

<h4><font size=3>📚 Areas</font></h4>

```dataview
TABLE
FROM "20-29 Areas"
SORT file.name ASC
```
</div>

<div class="double-line-all">

<h4><font size=3>📂 Projects</font></h4>

```dataview
TABLE
FROM "30-39 Projects"
SORT file.name ASC
```
</div>
</div>
<br>

___

<br>
<center>
<p> <font size=2> Made with ❤️ by Gemini</font></p>
</center>

<style>
    .date {
        color: #E5588D; 
    }
    .parent-container {
        display: flex;
        justify-content: space-between;
    }
    .left-container {
        flex-basis: 70%;
        padding-right: 10px;
    }
    .right-container {
        flex-basis: 30%;
        padding-left: 10px;
    }
    .double-line-all {
        border: 1px solid #ddd;
        border-radius: 5px;
        padding: 15px;
        background-color: #F7F7F7;
    }
	.parent-container-grid {
	    display: grid;
	    grid-template-columns: repeat(2, 1fr);
	    grid-gap: 20px;
	}
</style>
