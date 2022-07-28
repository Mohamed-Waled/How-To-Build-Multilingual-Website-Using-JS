# How To Build Multilingual Website Using JavaScript & JSON

In This Repo I'll Discuss How To Build Multilingual Website Using JS

## Table of Contents

- [Idea Explanation](#idea-explanation)
  - [Give it a Try First](#give-it-a-try-first)
- [The Process](#the-process)
  - [JSON Files](#JSONFiles)
  - [Prepare HTML File](#PrepareHTMLFile)
  - [Write Your JS Function](#Writeyourjsfunction)
  - [Build The Button](#buildthebutton)
  - [Use Local Storage](#uselocalstorage)
- [Author](#author)
- [Contributes](#contributes)

## Idea Explanation

First of all, we will use JSON and JS to build this. The idea is that we will write every word in the website in the JSON file as a value and the key will be whatever you want next we will write another JSON file with the duplicate keys but we will change every value with its alternative in the language we want to, then we will add a data attribute in every element in HTML file that we want to translate with the key name from the JSON file and delete the text inside the HTML element last but not least we will write our JS function that iterates on every HTML element and push to it the value of the key that we reported earlier in the data attribute and when we need to change the language we will click a button we will build to change the path of the JSON file to bring another language and push it instead of the languages we use now.

### Give it a Try First

I think if you tried to do it yourself first it will be more valuable for youe both search skills and programing skills so i advise you to search about these topics first and try to do it yourself and after that come back and see what i've done.

- How to make a maltilingual JS application using JSON.

**What I Recommend to You to Search About**

- How to access JSON file using JS.
- How to loop over JSON keys using JS.
- How to select every DOM element using JS.
- How to loop over every DOM element using JS.
- How to access elements attributes and loop over them.

## The Process

### JSON Files

1. You need to write every word in the website as a value of a key of your chose in JSON as Example if we will make English Arabic website:
   - I've a h1 element wants ti write it it **Hello, World!**.
   - Open your JSON file and write in it like that:
   ```
   {
       "key":"value"
       "greeting":"Hello, World!"
   }
   ```
   - Continue on every element you have in the HTML file.
2. You need to write another JSON file with the same keys in your last file but the value will be the other language in this example it will be arabic.
   - Open your new JSON file and write in it like that:
   ```
   {
       "the same key as previous":"the other language word"
       "greeting":"مرحبا, بالعالم!"
   }
   ```
   - Continue on every element you have in HTML file that you previously wrote in the English file.
3. Nice This Step Is Done Now.

### Prepare HTML File

1. Get into your HTML file and give every element you want to translate and you previously wrote it in the two JSON files a data attribute like that:
   - Get your HTML element
   ```
   <h1>Hello, World!</h1>
   ```
   - But a data attribute with any name like data-lang as short for languages with tha same key you previously gave to the text in the element
   ```
   <h1 data-lang="greeting">Hello, World!</h1>
   ```
2. Delete the textNode from your element like that:
   ```
   <h1 data-lang="greeting"></h1>
   ```
3. Do it for every elemt has textNode and you want to translate and you previously wrote in the JSON files.
4. Nice This Step Is Done Now.

### Write Your JS Function

Now we are about to write our translation JS function First of all the idea is that the function get access of the JSON files and read every key of them and get access of the HTML file and read every data-lang atribute value and when the function find a similar key as like as a data-lang attribute value it pushs the value of the key from the JSON file as an innerHTML or a textNode into the element that it found the match in it so the HTML now has its textNode again so lets do it.

1. Now you need to make the function and get access of your JSON file and for this I prefared to use fetch().  
   P.S. You will need to use Live Server or any way to test this way on a local server before you lunche it.  
   P.S. You will need to upload you JSON file on any API servies before you use it , GitHub Worked perfectly with me but make sure to get the raw data link [JSONbin](https://jsonbin.io/) Worked perfectly too.

```
function translate() {
    fetch(JSON file Path or link)
    .then ((response) => {
        return response.json(); // To return the data from the JSON file
    })
    .then ((jsondata) => {
        here we will write what to do with this json data
    })
    .catch ((error) => {
        return console.log(errer); // To catch any error
    })
}
```

2. Now we have the json data in our hands and want to use it
   - First we need to loop over the data init to get every key.
   ```
   function translate() {
   fetch(`https://raw.githubusercontent.com/Mohamed-Waled/webSite/main/languages/en.json`)
   .then ((response) => {
       return response.json(); // To return the data from the JSON file
   })
   .then ((jsondata) => {
       for (const key in jsondata) {
           here we will write what to do with the keys from json data
       }
   })
   .catch ((error) => {
       return console.log(errer); // To catch any error
   })
   }
   ```
3. Now we need to lopp over every DOM element and its attributes to find out witch elemnt has the needed attribute that have the same value as the key so we can push the key's value into the element HTML.

```
   function translate() {
    let allDom = document.querySelectorAll("*"); // Select every DOM element

   fetch(`https://raw.githubusercontent.com/Mohamed-Waled/webSite/main/languages/en.json`)
   .then ((response) => {
       return response.json(); // To return the data from the JSON file
   })
   .then ((jsondata) => {
       for (const key in jsondata) {
        allDom.forEach((element) => {
          for (const attr of element.attributes) {
            if (element.hasAttribute("data-lang")) {
              if (attr.name === "data-lang") {
                if (attr.value === key) {
                  element.innerHTML += jsondata[key];
                }
              }
            }
          }
        });
       }
   })
   .catch ((error) => {
       return console.log(errer); // To catch any error
   })
   }
```

4. Now we will add a variable that will help us when we build the button to change the languages and will use it in the fetch to pass the file name that have the language.

```
function translate(language) {
  let lang = language;
  let allDom = document.querySelectorAll("*");

  fetch(
    `https://raw.githubusercontent.com/Mohamed-Waled/webSite/main/languages/${lang}.json`
  )
    .then((response) => {
      return response.json();
    })
    .then((jsondata) => {
      for (const key in jsondata) {
        allDom.forEach((element) => {
          for (const attr of element.attributes) {
            if (element.hasAttribute("data-lang")) {
              if (attr.name === "data-lang") {
                if (attr.value === key) {
                  element.innerHTML += jsondata[key];
                }
              }
            }
          }
        });
      }
    });
}
```

### Build The Button

1. Fell free to design you desired button to change the languages I choosed to build it from input check box as it is easier to write the logic after that.
2. I've made css class with the style I need to be applied to the page when the other language is applied because Arabic is right to left language
3. Write what you need to be done when you click the button

```
function changeLanguagesButton() {
  let checkBoxlang = document.querySelector(".checkboxlang");
  let body = document.querySelector("body");

  checkBoxlang.addEventListener("change", () => {
    if (checkBoxlang.checked) {
      body.classList.add("rtl");
      body.setAttribute("dir", "rtl");
      window.location.reload();
      translate("ar");
    } else {
      body.classList.remove("rtl");
      body.removeAttribute("dir", "rtl");
      window.location.reload();
      translate("en");
    }
  });
  });
}
```

4. Be aware that the function you will write depends so much on the way you wrote the HTML & CSS of the button.

### Use Local Storage

Now you need to add your last choosen language on the website to the local storage so when you get back to it you find your website with the last choosen language.

1. So we will make a local storsge item and set it so we can get the data out of it again

```
function addLanguagetoLocalStorage() {
  let checkBoxlang = document.querySelector(".checkboxlang");
  let arabic = false;

  checkBoxlang.addEventListener("change", () => {
    if (checkBoxlang.checked) {
      arabic = true;
      window.localStorage.setItem("isArabic?", arabic);
    } else {
      arabic = false;
      window.localStorage.setItem("isArabic?", arabic);
    }
  });
}
```

2. Now we need to get what language will the website get onload so we will write anothe function to do so.

```
function onLoadLanguages() {
  let isArabic = window.localStorage.getItem("isArabic?");
  let checkBoxlang = document.querySelector(".checkboxlang");
  let body = document.querySelector("body");

  window.addEventListener("load", () => {
    if (isArabic === "true") {
      body.classList.add("rtl");
      body.setAttribute("dir", "rtl");
      checkBoxlang.checked = true;
      translate("ar");
    } else {
      body.classList.remove("rtl");
      body.removeAttribute("dir", "rtl");
      checkBoxlang.checked = false;
      translate("en");
    }
  });
}
```

**And thats it now when you click the button the languages will change and when you restart you website it will remain the same even if you changes the session. You can try this in [this website here](https://github.com/Mohamed-Waled/webSite)**

## Author

- Frontend Mentor - [@Mohamed-Waled](https://www.frontendmentor.io/profile/Mohamed-Waled)
- Linkedin - [@mohamed-waled](https://www.linkedin.com/in/mohamed-waled-82a51a1bb/)
- Leet Code - [@MohamedWaled](https://leetcode.com/MohamedWaled/)

## Contributes

If you need an English Arabic, Arabic English Translator feel free to call Mr.[Mohamed Abdallah](https://www.linkedin.com/in/mohamed-abdallah-a94158222/), He translated this website [here](https://github.com/Mohamed-Waled/webSite) for me check it out in Arabic, He is so professional and respects his deadlines, For any business translation deals, You can reach him [from here](mailto:mohammedabdallah.badr@gmail.com)

