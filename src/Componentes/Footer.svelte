<script>

</script>

<main>
    <main>
        <div class="footer">
            <div class="row">
                <div class="col-12 col-sm-3">
                    <p class="pri">Aviso de privacidad / Contacto</p>
                </div>
                <div class="col-12 col-sm-3 d-flex justify-content-center align-items-center im">
                    <img class="logo" src="img/logo-sochi.png" alt="">
                </div>
                <div class="col-12 col-sm-6 d-flex justify-content-end align-items-center">
                    <div class="redes">
                        <div class="icono mobli"><img src="img/mobli-icon.png" alt=""></div>
                        <div class="icono facebook"><i class="bi bi-facebook"></i></div>
                        <div class="icono teitter"><i class="bi bi-twitter"></i></div>
                        <div class="icono youtube"><i class="bi bi-youtube"></i></div>
                    </div>
                </div>
            </div>
        </div>
    </main>
    
</main>

<style>
    .logo{
        margin-left: 400px;
    }
    .pri{
        margin-left: 50px;
        margin-top: 20px;
    }
    .footer {
    background-color: black;
    padding: 20px;
    font-family: 'Exo';
}

.footer p {
    color: white;
}

.redes {
    display: flex;
    gap: 10px; 
    margin-right: 100px;
}

.icono {
    background-color: transparent;
    width: 40px;
    height: 40px;
    display: flex;
    justify-content: center; 
    align-items: center; 
    border-radius: 5px;
}

.icono img {
    max-width: 100%; 
    max-height: 100%; 
    display: block; 
}

.icono i {
    color: white; 
    font-size: 24px; 
}

.facebook{
    background-color: #3b5998;
}
.teitter{
    background-color: #1da1f2;
}
.youtube{
    background-color: #ff0000;
}
.mobli{
    background-color:#6CA9E9 ;
}
/* Estilos para dispositivos móviles */
@media screen and (max-width: 768px) {
    .logo {
        margin-left: 50px; 
    }

    .pri {
        margin-left: 20px; 
        margin-top: 10px; 
    }

    .footer {
        padding: 10px; 
    }

    .redes {
        margin-right: 20px; 
    }

    .icono {
        width: 30px; 
        height: 30px; 
    }

    .icono i {
        font-size: 20px; 
    }
}

</style>