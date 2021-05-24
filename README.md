
# leet-list

## Project description

Leet list displays a list of employees, the data is fetched from an API. 

Various filter and sorting functions has been implemented. 

Images are fetched from the server when needed, and if the image URL does not exists it is replaced by a placeholder image. 

Links to social media is displayed if they exist in the fetched data.

Leet List is written using Vue.JS and Bootstrap.


## Project setup

```

npm install

```

  

### Compiles and hot-reloads for development

```

npm run serve

```

  

### Compiles and minifies for production

```

npm run build

```

## What did I do?

- **Responsive design**
-- When creating a web app, I want it to use the advantages there is for a web based application and have it to be runnable on different devices, like a iPad.

- **Sort by name and office**
-- I'm not 100% satisfied with the sorting function, If I had more time and a Slack-channel full of colleagues I would ask for help to review and pair code this function. But I'll leave it in the code, it at least shows how I would implement it UI wise.

- **Filter by name and office**
-- Filters name and office with computed properties for a live update of the employees list after typing each letter.

- **Available on a free public url**
-- It's easy and free to set up a quick static website on Azure. And the cloud is the new black? https://thankful-forest-01ce5b003.azurestaticapps.net/#

- **CI/CD pipeline from your repo**
-- Quick and easy to set up, and I like the concept of "Always be shipping!"

- **Pagination**
-- With over 200+ rows a pagination function is nice to have. When running on a smaller device it changes to Next/Previous.

- **Works in Chrome, Firefox, Edge**
-- Same reason as responsive design, web applications should be runnable on various web browsers, thats the strength of web based applications.

**Total points: 9**, *but I didn't get at least two points from _testin/QA.* 

I would like to do the Unit Test part also, but as explained further down, I don't want to submit anything that I'm not confident that I actually knows, not just copy pastes from Stack Overflow. 

## What did I not do?
- **No UI framework used**
-- I'm not very good at CSS, and wanted to use a UI framework to do all the heavy lifting.

- **Don’t use our API, build your own API by scraping the current page and setting up a local backend server.**
-- I've done some hobby work with Node.JS, but I think the current API is good enough. If I had created a backend of my own I've probably implemented a basic filter function for enabled employees.

- **Unit tests for existing functionality**
-- This is the function I most of all wanted to do, but I haven't worked with a JS Testing framework for Unit Tests yet. I've done another project in C# where I used Unit Tests, so I understand the concept at least. (https://github.com/joakim-lundbeck/FallOffTable) *But I don't want to submit anything that I just learned by copy pasting stuff from Stack Overflow.* This would also give me extra 2 point in the last category.

## What would I do different?

- I would give the sorting function more love, with the help of a colleague 
- Ask for more documentation of the backend API, is there more filter parameters I could use?
- Fancy Animations. Because it should always look nice. I've been mostly working with applications that displays data, and no one really cares about fancy animations. 
- Better GIT Commits, sometimes I loose track of how much code I write, so I commit in to large chunks. 