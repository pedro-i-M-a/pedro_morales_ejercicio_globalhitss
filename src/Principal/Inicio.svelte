<script>
// @ts-nocheck
import { onMount, onDestroy } from 'svelte';
// FUNCION PARA LA FECHA
const fechaObjetivo = new Date('2024-12-31T00:00:00');
let dias = 0;
let horas = 0;
let minutos = 0;
let segundos = 0;

const Fecha = () =>{
const fechaActual = new Date();
const diferencia = fechaObjetivo - fechaActual;

 dias = Math.floor(diferencia / (1000 * 60 * 60 * 24));
 horas = Math.floor((diferencia % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
 minutos = Math.floor((diferencia % (1000 * 60 * 60)) / (1000 * 60));
 segundos = Math.floor((diferencia % (1000 * 60)) / 1000);
}
// PARA ACTUALIZAR LA FECHA CADA SEGUNDO
let actualizarFecha;
  onMount(() => {
    Fecha();
    actualizarFecha = setInterval(Fecha, 1000);
  });

  onDestroy(() => {
    clearInterval(actualizarFecha);
  });

// FUNCION PARA LOS VIDEOS
let videoId = "w81Yj4uWir0?si=BakpjqZgh68u6rmd";
// https://youtu.be/xczfk5mMh64?si=VJDT3d90mEQbSDQl
// https://youtu.be/kDrKCBVIU9M?si=oPW3WaAibKj18kxl
// https://youtu.be/ckEYQkGl128?si=Kvmx23P3MNRfquo5
const videos = [
    { id: "w81Yj4uWir0?si=BakpjqZgh68u6rmd", image: "team-latam.png", title: "TEAM LATAM" },
    { id: "xczfk5mMh64?si=VJDT3d90mEQbSDQl", image: "travel-meets-fashion.png", title: "TRAVEL MEETS FASHION" },
    { id: "kDrKCBVIU9M?si=oPW3WaAibKj18kxl", image: "velocidad-riesgo.png", title: "VELOCIDAD Y RIESGO" },
    { id: "ckEYQkGl128?si=Kvmx23P3MNRfquo5", image: "experiencia.png", title: "EXPERIENCIA MULTIMEDIA" }
  ];
  const cambiarVideo = (nuevoVideoId) => {
    videoId = nuevoVideoId;
  }
</script>

<main>
    <div class="vid-pri">
        <!-- DIV PARA CONTADOR DE DÍAS HASTA el día 31 de diciembre a las 00:00 horas. -->
        <div class="faltan">
            <h1>Faltan</h1>
            <div class="row">
                <div class="col">
                    <div class="contador">
                        <div class="numero">{dias}</div>
                        <div class="etiqueta">DÍAS</div>
                    </div>
                </div>
                <div class="col">
                    <div class="contador">
                        <div class="numero">{horas}</div>
                        <div class="etiqueta">HRS</div>
                    </div>
                </div>
                <div class="col">
                    <div class="contador">
                        <div class="numero">{minutos}</div>
                        <div class="etiqueta">MIN</div>
                    </div>
                </div>
                <div class="col">
                    <div class="contador">
                        <div class="numero">{segundos}</div>
                        <div class="etiqueta">SEG</div>
                    </div>
                </div>
            </div>
            
        </div>
       <!-- DEV PARA MOSTRAR VIDEOS -->
       <div class="reproductor">
            <!-- svelte-ignore a11y-missing-attribute -->
            <iframe
                width="560"
                height="315"
                src={`https://www.youtube.com/embed/${videoId}?autoplay=1`}
                frameborder="0"
                allow="autoplay; fullscreen"
                allowfullscreen
                autoplay
                muted
          ></iframe>
        </div>
    </div>

    <!-- DIV PARA LOS BOTONES DE SELECCION DE VIDEOS -->
    <div class="botones-videos">
        <h2>CLARO SPORTS EN SOCHI 2014</h2>
        <div class="buttons-container">
            {#each videos as video}
            <div class="button-wrapper">
              <button on:click={() => cambiarVideo(video.id)}>
                <img src={`img/${video.image}`} alt={video.title}>
              </button>
              <p>{video.title}</p>
            </div>
          {/each}
        </div>
    
</main>

<style>
    /* ESTILO PARA EL DIV DE EL VIDEO Y EL CONTADOR */
.vid-pri {
    background-color: black; 
    background-image: url('/img/background.jpg'); 
    background-size: 70%;
    background-repeat: no-repeat; 
    background-position: center top ; 
    padding-top: 40%; 
    padding-left: 10%; 
    padding-right: 10%; 
    position: relative;
    display: grid;
    grid-column: 1fr;
    font-family: 'Exo';
}
/* Estilos para los números encima de los círculos */
.faltan{
    position: absolute; 
    top: 10%; 
    left: 50%; 
    transform: translate(-50%, -50%);
    color: white; 
}
.faltan h1{
    margin-left: 40%;
    margin-top: 10%;
    font-family: 'Exo';
}
.contador {
   border: 2px solid white; 
   border-radius: 50%; 
   width: 70px; 
   height: 70px; 
   display: flex;
   flex-direction: column;
   justify-content: center;
   align-items: center;
   font-family: 'Exo';
}

.numero {
   font-size: 2rem;
   text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
   /* border: 2px solid white; */
   font-family: 'Exo';
  
}

.etiqueta {
   font-size: 1rem;
} 
/* ESTILOS PARA EL AJUSTE DEL VIDEO */
.reproductor {
        position: absolute; 
        top: 60%; 
        left: 50%; 
        transform: translate(-50%, -50%); 
       
    }
    

/* ESTILOS PARA LOS BOTONES PARA CAMBIAR LOS VIDEOS */
.botones-videos {
    background-color: #232323;
    padding: 20px; 
    font-family: 'Exo';
}

.botones-videos h2 {
    margin-bottom: 10px;
    text-align: center;
    color: white;
}

.buttons-container {
    display: flex;
    justify-content: center;
}

.button-wrapper {
    text-align: center;
    margin: 0 10px; 
}

.button-wrapper button {
    border: none;
    background: none;
    cursor: pointer;
}
/* ANIMACION */
.button-wrapper button:hover{
    animation:jello-horizontal .9s linear both}
     @keyframes jello-horizontal{0%
    {transform:scale3d(1,1,1)}
    30%{transform:scale3d(1.25,.75,1)}
    40%{transform:scale3d(.75,1.25,1)}
    50%{transform:scale3d(1.15,.85,1)}
    65%{transform:scale3d(.95,1.05,1)}
    75%{transform:scale3d(1.05,.95,1)}
    100%{transform:scale3d(1,1,1)}
}

.buttons-container p {
    color: white;
    margin-top: 5px;
}
.button-wrapper{
    animation:scale-up-center 0.4s; 
} 
@keyframes scale-up-center
{ 
    0%{transform:scale(.5)} 100%{transform:scale(1)}
}


/* Estilos para dispositivos móviles vid-pri */
@media screen and (max-width: 800px) {
  .vid-pri {
    padding-top: 90%; 
    padding-left: 5%; 
    padding-right: 5%; 
    background-size: 100%;
  }
}
/* Estilos para dispositivos móviles faltan */
@media screen and (max-width: 800px) {
  .faltan {
    top: 15%; 
    transform: translate(-50%, -50%);
    
  }

  .faltan h1 {
    margin-left: 30%; 
    margin-top: 5%; 
    font-size: 1.5rem; 
  }

  .contador {
    
    width: 40px; 
    height: 40px; 
  }

  .numero {
    font-size: 1.2rem; 
  }

  .etiqueta {
    font-size: 0.8rem; 
  }
}


/* Estilos para dispositivos móviles reproductor*/
@media screen and (max-width: 800px) {
  .reproductor iframe  {
    max-width: 100%; 
    height: auto;
    /* margin-top: 50%; */
  }
}

/* Estilos para dispositivos móviles botones-videos*/
@media screen and (max-width: 800px) {
  .botones-videos {
    padding: 10px; 
  }

  .botones-videos h2 {
    font-size: 1.2rem; 
  }

  .buttons-container {
    flex-direction: column;
  }

  .button-wrapper {
    margin: 10px 0; 
  }
}

</style>