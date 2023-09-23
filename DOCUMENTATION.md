### Sidebar :

# export default function Sidebar(props) {
    const noteElements = props.notes.map((note, index) =>

    Here Props used :
    Here note used :
    Here index used: 


# <div key={note.id}>

    Here Key used :

# <div 
className={`title ${note.id === props.currentNote.id ? "selected-note" : ""}`}
onClick={() => props.setCurrentNoteId(note.id)}>
<h4 className="text-snippet">
  {note.body.split("\n")[0]}
</h4>
<button className="delete-btn" onClick={(event) => props.deleteNote(event, note.id)}>
<i className="gg-trash trash-icon"></i>
</button>
</div>

    Here onClick={() => props.setCurrentNoteId(note.id)} used: 
    Here {note.body.split("\n")[0]} used :
    Here props.deleteNote(event, note.id) used :
    Here <i className="gg-trash trash-icon"></i> used : 



            
