# 快去 <mark style="background: #FF5582A6;">Git Pull</mark> 一下

```dataviewjs
const calendarData = {
year: 2023,
colors: {
blue:        ["#8cb9ff","#69a3ff","#428bff","#1872ff","#0058e2"], // first entry is considered default if supplied
green:       ["#c6e48b","#7bc96f","#49af5d","#2e8840","#196127"],
red:         ["#c6e48b","#c6e48b","#c6e48b","#c6e48b","#c6e48b"],
orange:      ["#ffa244","#fd7f00","#dd6f00","#bf6000","#9b4e00"],
pink:        ["#ff96cb","#ff70b8","#ff3a9d","#ee0077","#c30062"],
orangeToRed: ["#ffdf04","#ffbe04","#ff9a03","#ff6d02","#ff2c01"]
},
entries: []
}

for(let page of dv.pages()){
let color = "green"
let intensity = page.workload
calendarData.entries.push({
date: page.file.name,
color: color,
intensity: 1
})

}

renderHeatmapCalendar(this.container, calendarData)
```
```dataviewjs

dv.list(new Set(dv.pages().file.tags))

```
