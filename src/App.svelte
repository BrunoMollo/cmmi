<script>
  const key_words={
    OPF:['organi',  'activo'],
    OPD:['organi', 'activo'],
    OT:['organi', 'activo'],
    PP:['proyecto'],
    PMC:['proyecto'],
    VAL:['proyecto', 'cliente', 'aceptacion','producto de trabajo' ],
    VER:['proyecto','producto de trabajo' ],
  }

  let question=''

  const counts={
    OPF:0,
    OTD:0,
    OT:0,
    PP:0,
    PMC:0,
    VAL:0,
    VER:0,
  }
  
  $:{
    for(let area in counts){
      counts[area]=0
      key_words[area].forEach(word=>{
        if(question.includes(word)){
          counts[area]++ 
        }
      })
          
    }
  }
</script>


<h1>Holaa</h1>
<textarea bind:value={question}></textarea>


<pre>
  {JSON.stringify(counts)}
</pre>
