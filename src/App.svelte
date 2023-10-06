<script lang='ts'>
    import { each } from "svelte/internal";

  const key_words={
    OPF:['organi',  'activo', 'analizar', 'mejoras', 'cambios', 'oprtunidades de mejora', 'procedimientos', 'fuertes', 'endebles', 'objetivo'],
    OPD:['organi', 'activo', 'definir', 'repositorio', 'analizado', 'cambios', 'no publicado', 'realizado', 'procedimientos' ],
    OT:['organi', 'activo'],
    PP:['proyecto','primera vez', 'inicio', 'objetivo', 'puntos de funcion', 'roles', 'plazo' ],
    PMC:['proyecto', 'retraso', 'reunión de avance', 'plan','inconvenientes', 'problema', 'corroborar', 'Firefox', 'controles', 'mail' ],
    VAL:['proyecto', 'cliente', 'aceptacion','producto de trabajo', 'diagramas de secuencia', 'casos de uso', 'caso de uso' ],
    VER:['proyecto','producto de trabajo','diagramas de secuencia', 'casos de uso', 'caso de uso', 'inspección', 'dss' ],
  }

  let question=''

  const counts={
    OPF:0,
    OPD:0,
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


<h1>Adivinador de CMMI</h1>

<span>Vos pega la pregunta, el que tenga el numerito am alto sera el mas probalbe (espero)</span>
<pre>
  {JSON.stringify(counts)}
</pre>
<textarea bind:value={question}></textarea>


<style>
textarea {
  width: 100%;
  height: 200px;
  font-size: 1.5em;
}
</style>

