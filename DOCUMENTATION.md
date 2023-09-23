### Sidebar

```jsx
export default function Sidebar(props) {
  const noteElements = props.notes.map((note, index) => (

Props used:

props.notes
props.currentNote
Note used:

note
Index used:

index
Key used:

note.id
onClick used:

() => props.setCurrentNoteId(note.id)
{note.body.split("\n")[0]} used:

{note.body.split("\n")[0]}
props.deleteNote(event, note.id) used:

props.deleteNote(event, note.id)
<i className="gg-trash trash-icon"></i> used:

<i className="gg-trash trash-icon"></i>


  <div key={note.id}>
    <div
      className={`title ${note.id === props.currentNote.id ? "selected-note" : ""}`}
      onClick={() => props.setCurrentNoteId(note.id)}
    >
      <h4 className="text-snippet">
        {note.body.split("\n")[0]}
      </h4>
      <button className="delete-btn" onClick={(event) => props.deleteNote(event, note.id)}>
        <i className="gg-trash trash-icon"></i>
      </button>
    </div>
  </div>



