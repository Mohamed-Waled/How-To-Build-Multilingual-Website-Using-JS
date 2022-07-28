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

## Idea Explanation

First of all, we will use JSON and JS to build this. The idea is that we will write every word in the website in the JSON file as a value and the key will be whatever you want next we will write another JSON file with the duplicate keys but we will change every value with its alternative in the language we want to, then we will add a data attribute in every element in HTML file that we want to translate with the key name from the JSON file and delete the text inside the HTML element last but not least we will write our JS function that iterates on every HTML element and push to it the value of the key that we reported earlier in the data attribute and when we need to change the language we will click a button we will build to change the path of the JSON file to bring another language and push it instead of the languages we use now.

### Give it a Try First

