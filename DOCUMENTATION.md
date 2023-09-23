
# 1. Sidebar Component
* notes={notes}
* currentNote={currentNote}
* setCurrentNoteId={setCurrentNoteId}
* newNote={createNewNote}
* deleteNote={deleteNote}

## a) function Sidebar(props) 
### {const noteElements = props.notes.map((note, index) => ()

* props: In the example you provided, the Sidebar component uses props to receive the notes and currentNote data from its parent component. This allows the Sidebar component to render a list of notes, with the current note highlighted, without having to know how the data is being managed.

* notes: The Sidebar component receives a notes prop, which suggests that it is responsible for rendering a list of notes from ana array .
* index: The index parameter is useful for identifying each element in the props.notes array. This can be useful for things like rendering a unique key for each element, or for conditionally rendering certain elements. In the example you provided, the index parameter is used to generate a unique key for each <div> element.This is important because React uses keys to track the identity of elements over time. This allows React to efficiently update the UI when the data changes.


## b) div
                
* className={`title ${note.id === props.currentNote.id ? "selected-note" : ""}`}
* onClick={() => props.setCurrentNoteId(note.id)}>
* h4, {note.body.split("\n")[0]}
* button onClick={(event) => props.deleteNote(event, note.id)}>
* <i></i>
</button>



## c) return ()
  * button,onClick: ={props.newNote}


# 2. Editor Component

## 2.1) Imports: 
* ReactMde from "react-mde": ReactMde is a React Markdown editor component, a simple yet powerful and extensible component that can be used to create rich Markdown editors in React applications.

* Showdown from "showdown": Showdown is a JavaScript library that converts Markdown to HTML.

## 2.2) function Editor({ currentNote, updateNote }) 
   ### {const [selectedTab, setSelectedTab] = React.useState("write")

   * currentNote:
   * updateNote:
   * [selectedTab, setSelectedTab]:
   * "write":

## 2.3)  converter = new Showdown.Converter({})
  * tables: true :
  * simplifiedAutoLink: true : 
  * strikethrough: true: 
  * tasklists: true:

## 2.4) ReactMde
* value={currentNote.body} : 
* onChange={updateNote} : 
* selectedTab={selectedTab} : 
* onTabChange={setSelectedTab} : 
* generateMarkdownPreview={(markdown) => Promise.resolve(converter.makeHtml(markdown))} : 
* minEditorHeight={80} : 
* heightUnits="vh" : 
        



