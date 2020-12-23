# Vue todo
https://todovueapplication.herokuapp.com/
Implemented through Vue, making the classic to-do application, letting you set tasks (todos), set
them as complete, delete single task, delete all complete task, delete all tasks.
Follow the hosted link above, or do the following to test locally.

## Test Locally
- Clone repository, navigate to correct folder
- Type ``` npm install "&&" npm run serve ``` in the terminal
- See it live on ``` http://localhost:8080/ ```

# Article
- [Contents of App](#contents)
- [Tech](#tech-usage-and-reasoning)
- [Challenges during project, and how I faced them](#challenges-faced)
- [Design: Illustrations and Color](#design)
- [An in-depth description about the content of the project](#full-description)

# Contents
* Add Tasks
* Toggle Tasks State (pending to complete or complete to pending)
* Remove All Tasks or All Complete Tasks
* LocalStorageAPI, tasks saved in browser cache - expect to see the same result when you revisit.

# Tech Usage and Reasoning
Like many developers may agree on, learning a new language or framework is always exiting. In
combination, creating a todo-list will usually give a good start to the learning, getting familiar to
multiple important topics in a such and small application. As I wanted to learn more about Vue, I
decided to do exactly so - dive into the framework attempting to learn.

# Challenges Faced
As mentioned in the section above, right from the get-go there was a really clear task ahead of me.
The direct challenges I faced was therefor not related to my goal, but related to my beginning
experience towards the Vue framework.

## Passing down props - parent to child
Being used to working with React made me immediately face the challenge on how I could pass
down properties to components further down the line, as an example passing a list to a child
component in react could be made by the following:

```
<section>
<ChildComponent foolist={foolist} />
</section>
```

On the other side, with Vue data binding can be done differently. For example purpose and
comparability with the React implementation above, a passing of props could be done like the
following.

```
<template>
[..]
<ChildComponent v-bind:foolist="foolist" />
</template>
```

# Design
My intention when creating this todo-application was keeping the experience as light and simple as
possible. When using a todo-application it is highly likely that it for simplifying and structuring to
make situations more controlled, to then have an UI/UX that is confusing would only clash with its
purpose.

Classic gradients are therefor utilized, bright colors for buttons that have impactful actions. Green for
active choices that is recommended to do(add a task), red for task that should only be used when
meaning, having the color red for increased alertness - this is placed on the delete functions.
The tasks itself are not what should pull the most attention, therefor given a mild and faded grey
color, with the intention of maintaining the simplicity. 

## Responsive Design
<p align="center">
<img src="https://i.imgur.com/w0c2DXj.png" alt="vue todo vuetodo bragerosberg" />
<img src="https://i.imgur.com/Btt1CDg.png" alt="vue todo vuetodo bragerosberg" />
</p>

# Full Description
Step-by-step walkthrough of the functionality.

### Landing Page
You'll start by seeing a form at the top with an input field and three colored buttons. Each button will
be explained further down. You'll also see a task beneath saying ```There are currently no tasks
added, type a task to see it above.```.

### I want ot add a task
To start, type inside the input field where it says ```Please write your task here```. Whenever you have
written what you desire, go ahead and submit the task to the list. To do so you simply click the green
button that is saying ```Add Todo``` or press the key ```Enter```

### I want to set a task as complete
On the list beneath the input form where you wrote your task, you can see all the entries you have
written in descending order. To set a task as complete, simply click on the box of which your task is
written inside.
Did you toggle a task as complete by mistake? No worries, click again and toggle it back.

### How do I remove tasks from the list?
When you have done the step above, marking tasks as complete. You can click the ```X``` on the righthand side to delete it from the display. 
Do you have many entries that are complete and wanting to delete? Lets use one of the buttons at
the top. There are two red buttons, the first one on the right that says ```Clear Complete``` will
remove all entries of task that are set to the state of complete.

### I want to redo the entire list
If you'd like to start over, you can use the second red button - this wil reset the entire list. Simply
click the button ```Clear List```, however be careful to not use this if not intended, as this will erase
everything. It is also possible to start over if you have deleted all tasks manually.

### Will my tasks be saved so I can see them when I come back later?
Yes, they will. All tasks are saved in your local browser cache (LocalStorageAPI), meaning when you
come back to the hosted website the browser will check if you have any tasks from before, and If you
do they'll load.
Whenever you ```Clear List```, ```Clear Complete``` or clear individual tasks they will be deleted from
the browser and not occupy any storage.

### Get in touch with me:
[<img align="left" style="margin-left: 10px;" alt="codeSTACKr | LinkedIn" width="40px"
src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" />][linkedin]
[<img align="left" style="margin-left: 10px;" alt="codeSTACKr.com" width="40px"
src="https://raw.githubusercontent.com/iconic/open-iconic/master/svg/globe.svg" />][website]
<a href="mailto:bragecontact@gmail.com"><img width="40px" className="homepage__contact"
alt="gmail" src="https://i.imgur.com/mo4E0Fb.png"/></a>

[linkedin]: https://www.linkedin.com/in/brage-rosberg/
[website]: https://www.bragerosberg.com
