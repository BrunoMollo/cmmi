<script lang='ts'>
  const key_words={
    OPF:['organi',  'activo'],
    OPD:['organi', 'activo'],
    OT:['organi', 'activo'],
    PP:['proyecto'],
    PMC:['proyecto', 'retraso', 'reunión de avance', 'plan'],
    VAL:['proyecto', 'cliente', 'aceptacion','producto de trabajo', 'diagramas de secuencia', 'casos de uso', 'caso de uso' ],
    VER:['proyecto','producto de trabajo','diagramas de secuencia', 'casos de uso', 'caso de uso', 'Inspección' ],
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
      if(key_words[area]===undefined) continue
      key_words[area].forEach(word=>{
        const regex= new RegExp(word, 'i')
        if(question.match(regex)){
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
