# Technology Overview

### ☝️ You don't have to learn or know all the mentioned stuff

### All the fundamentals like Request Response Pattern, HTTP, URLs etc. are the same no matter which language or Architecture is used 

<img width="1009" alt="overview" src="https://user-images.githubusercontent.com/10595723/127164695-c489d933-a785-4546-b7ee-4f5186810971.png">

# Replacements

<img width="821" alt="Screenshot 2021-07-27 at 17 10 31" src="https://user-images.githubusercontent.com/10595723/127179810-7e4df1c0-c06b-4bcb-b322-552b68e42897.png">

# Replacements for Tools, Libraries etc

<img width="997" alt="Screenshot 2021-07-28 at 15 37 36" src="https://user-images.githubusercontent.com/10595723/127332013-903957df-c4e3-4dd0-8361-b53efab9e2ff.png">

# Additional Tools, Libraries etc

### CSS 
* [SASS](https://sass-lang.com/) 

#### style.scss -> you can nest elements in the sass file

```css
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```
#### style.css -> This get's transformed to this CSS
```css
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```
* [Tailwind](Utility CSS)(https://tailwindcss.com/)
```css
<figure class="bg-gray-100 rounded-xl p-8">
  <img class="w-32 h-32 rounded-full mx-auto" src="/sarah-dayan.jpg" alt="" width="384" height="512">
  <div class="pt-6 space-y-4">
    <blockquote>
      <p class="text-lg font-semibold">
        “Tailwind CSS is the only framework that I've seen scale
        on large teams. It’s easy to customize, adapts to any design,
        and the build size is tiny.”
      </p>
    </blockquote>
  </div>
</figure>
```

### JavaScript

* [JQuery](https://jquery.com/) for DOM Manipulation - a little dated but you might see it in older apps

* [TypeScript](https://www.typescriptlang.org/) 

### Testing

* [Jest](https://jestjs.io/)
* [React Testing Tools](https://testing-library.com/docs/react-testing-library/intro/)

### React
* [Next JS](https://nextjs.org/) - React Framework for server side rendered applications

### Architecture
* SOLID Principles
* Domain Driven Design
* If you wanna read a book: Clean Code by Robert C. Martin

# From all the above i would learn Typescript and testing