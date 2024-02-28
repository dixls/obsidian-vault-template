---
created: <% tp.file.creation_date('YYYY-MM-DD' + ' ' + 'HH:mm') %>
tags: DailyNote
---
# <% moment(tp.file.title,'YYYY-MM-DD').format("dddd, DD MMMM YYYY") %>

<%*
var events = await app.plugins.getPlugin('ics').getEvents(moment(tp.file.title,'YYYY-MM-DD'));
events.sort((a,b) => a.utime - b.utime).forEach((e) => {
    const calendar = e.icsName.replace(" ","-");
    const callUrl = e.callUrl? ` [${e.callType}](${e.callUrl})` : '';
    const location = e.location? ` 📍 *(${e.location})*` : '';
    tR+=`- ${e.time}-${e.endTime} **${e.summary}**${location}${callUrl} #${calendar}\n`
    if (e.description) {
        const inlineDescription = e.description.replace(/(?:\r\n|\r|\n)/g," ").replace(/\s{2,}/g," ");
        tR+=`    - ${inlineDescription}\n`
    }
})
%>

> [!todo]+ Daily Quests  
> > ``` tasks
> > priority is above lowest
> > not done
> > path does not include {{query.file.path}}
> > ```
> > 

> [!abstract] General Notes  
> <% tp.file.cursor(1) %>

>[!note] Today's Notes
> >  ``` dataview
> > TABLE file.mtime as "Created"
> > WHERE file.mday = this.file.day
> > SORT file.mtime DESC
> > ```

>[!check] Finished To-Dos Today
> ``` tasks
>  done on <% tp.file.creation_date('YYYY-MM-DD') %>
