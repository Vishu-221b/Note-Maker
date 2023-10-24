
# 1. Sidebar Component
* notes={notes} notes is an array of notes that has been created and will be mapped to show every note on sidebar
* currentNote={currentNote}: It is also a function which is used to find out current note id  to setup css styles with it.
* setCurrentNoteId={setCurrentNoteId}: This is a lso a fnction used to set a particular note to set as current note.
* newNote={createNewNote}: It is a function defined to create a new note.
* deleteNote={deleteNote}: It is a function defined to delete a note.

  

## a) function Sidebar(props) 
### {const noteElements = props.notes.map((note, index) => ()

* props: In the example you provided, the Sidebar component uses props to receive the notes and currentNote data from its parent component. This allows the Sidebar component to render a list of notes, with the current note highlighted, without having to know how the data is being managed.

* notes: The Sidebar component receives a notes prop, which suggests that it is responsible for rendering a list of notes from ana array .
* index: The index parameter is useful for identifying each element in the props.notes array. This can be useful for things like rendering a unique key for each element, or for conditionally rendering certain elements. In the example you provided, the index parameter is used to generate a unique key for each <div> element.This is important because React uses keys to track the identity of elements over time. This allows React to efficiently update the UI when the data changes.


## b) div
                
* className={`title ${note.id === props.currentNote.id ? "selected-note" : ""}`}: We are setting the classname of the div to the only selected note div, so that we can highlight that note.

* onClick={() => props.setCurrentNoteId(note.id)}> : We are running a function here that we on clicking the note, will set the current note again.

  
* h4, {note.body.split("\n")[0]} : Split divides the whole string into an array of lines and it accesses the first [0] element to show.
* button onClick={(event) => props.deleteNote(event, note.id)}>: Function used to delete a note.
* <i></i>
</button>



## c) Return ()
* {props.newNote} : is a function which is getting accesses by props as argument provided in the sidebar component.
* newNote={createNewNote} this is the prop mentioned in the app.js sidebar component
* CreateNewNote is a function which will create a new note if clicked on the button + on sidebar.
* function createNewNote() {
        const newNote = {
            id: nanoid(),
            body: "# Type your markdown note's title here"
        }
        setNotes(prevNotes => [newNote, ...prevNotes])
        setCurrentNoteId(newNote.id)
    }
This is the whole function.




# 2. Editor Component
* currentNoteId && notes.length :
* currentNote={currentNote} : 
* updateNote={updateNote} : 


## 2.1) Imports: 

* ReactMde from "react-mde": ReactMde is a React Markdown editor component, a simple yet powerful and extensible component that can be used to create rich Markdown editors in React applications.

* Showdown from "showdown": Showdown is a JavaScript library that converts Markdown to HTML.
* 

## 2.2) function Editor({ currentNote, updateNote }) 
   ### {const [selectedTab, setSelectedTab] = React.useState("write")

   * currentNote: This is a prop we have passed to editor component from the app.js: currentNote: This prop likely represents the current note that the Editor component is meant to display or edit.
     
   * updateNote: This is the prop we have passes to editor from the app.js: This prop is likely a function that allows you to update the content of the note.
     
   * [selectedTab, setSelectedTab]:
   * selectedTab is a piece of state that you're defining using the useState hook. This state variable will hold the current selected tab value.
   * setSelectedTab is the function that allows you to update the selectedTab state.
   * "write":you're initializing the selectedTab state with the initial value "write". This means that when your component is first rendered, selectedTab will be set to "write".

## 2.3)  converter = new Showdown.Converter({})
  * tables: true :
  * simplifiedAutoLink: true : 
  * strikethrough: true: 
  * tasklists: true:
  * converter object you've created is configured to handle these specific Markdown features and convert them into their corresponding HTML representations. You can use this converter to parse Markdown text and generate HTML content with these features applied.

  * 

## 2.4) Return ReactMde : We return a REACTMDE editor inside a section, This ReactMde contains props and values such as:
* value={currentNote.body} : value is used to specify the current value or content of the editor, currentNote.body likely contains the Markdown content that you want to display and edit within the ReactMde component.

* onChange={updateNote} : onChange is a callback function that will be called whenever the content of the editor is changed.,
  updateNote is likely a function that updates the currentNote object with the new content. This function is called when the user edits the Markdown content in the editor.
  
* selectedTab={selectedTab} : selectedTab is used to determine which tab is currently selected within the ReactMde component.,based on the state value you've defined earlier (const [selectedTab, setSelectedTab] = React.useState("write")). It controls whether the user is in the "write" or another tab.
  
* onTabChange={setSelectedTab} : onTabChange is a callback function that is called when the user switches between tabs in the ReactMde component., setSelectedTab is used to update the selectedTab state when the user changes tabs.
  
* generateMarkdownPreview={(markdown) => Promise.resolve(converter.makeHtml(markdown))} : generateMarkdownPreview is a function that generates a preview of the Markdown content in real-time as the user types.
It takes the user's Markdown text as input (markdown) and uses the converter object (which we discussed earlier) to convert this Markdown into HTML.
The result of this conversion is returned as a Promise, which is then used to display the HTML preview of the Markdown content.

* minEditorHeight={80} :These props control the minimum height of the editor and specify that it should be measured in viewport height units (vh). 
* heightUnits="vh" :These props control the minimum height of the editor and specify that it should be measured in viewport height units (vh).


# 3. App.js

## 3.1) Imports
* Split from "react-split" : SPlit help in dividing the screen with a visible divider, for example to create a divider.
* { nanoid } from "nanoid" : This can be useful for generating unique IDs, identifiers for objects, keys in databases, or any situation where you need a unique string.
* import {Sidebar,Editor} : We are importing components in app.js to render them both in the screen.
* 

## 3.2) function App() {}
  * 1. const [notes, setNotes] = React.useState(() => JSON.parse(localStorage.getItem("notes")) || []) :
  * localStorage.getItem("notes") is used to retrieve a value stored in the browser's localStorage under the key "notes."
  * JSON.parse() is used to parse the retrieved value as JSON. If there is nothing stored in localStorage under the "notes" key or if the value is not valid JSON,
  * || [] is used to provide a default value of an empty array in case the value retrieved from localStorage is null or not present.

    
  * const [currentNoteId, setCurrentNoteId] = React.useState( notes[0]?.id) || "") : this code initializes currentNoteId with the id of the first note if it exists, or with an empty string if there are no notes or if the first note doesn't have an id.
    
  * const currentNote = notes.find(note => note.id === currentNoteId) || notes[0] :purpose of this code is to set currentNote to the note that has an id matching currentNoteId if such a note exists. If no matching note is found, it defaults to the first note in the notes array (or undefined if notes is empty).

    
  * React.useEffect(() => {localStorage.setItem("notes", JSON.stringify(notes))}, [notes]) :
  * The useEffect hook is used to perform side effects in React. It takes two arguments: a function and a dependency array.
  * Inside the useEffect, it uses localStorage.setItem to store the notes array in the browser's localStorage.
  * "notes" in this context is the key used to identify and retrieve the notes array when needed from the localStorage
  * The notes array is first converted to a JSON string using JSON.stringify because localStorage can only store string key-value pairs.
  * The [notes] dependency array indicates that this useEffect should only run when the notes array changes. If the notes array remains the same between renders, this effect won't execute.

    

## 3.3 Functions
* function createNewNote()
* function updateNote(text)
* function deleteNote(event, noteId)

## 3.4 Return 
* onClick={createNewNote} :
* Split :
* 


# 4. HTML

* meta charset="UTF-8" : 
* meta name="viewport" content="width=device-width, initial-scale=1.0" : 
* link rel="icon" href="/billi.jpg"/ :
* link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.css" : 
* link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/react-mde@11.5.0/lib/styles/css/react-mde-all.css" : 
* link rel="preconnect" href="https://fonts.googleapis.com" : 
* link rel="preconnect" href="https://fonts.gstatic.com" crossorigin : 
* link href="https://fonts.googleapis.com/css2?family=Karla:wght@400;700&display=swap" rel="stylesheet" : 

                    >



