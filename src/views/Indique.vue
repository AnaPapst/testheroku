<template>
<div class="in-tech__banner">
        <div class="">
            <div class="row">
                <div class="col-12 col-md-5 image">
                    <img src="../images/girlswhocode.png">
                </div>
                <div class="col-12 col-md-7">
                    <div class="in-tech__form">
                        <div class="container">
                            <div class="in-tech__form--title">
                                <h1>Indique uma futura dev!</h1>
                            </div>
                
                            <form class="in-tech__form__content indique">
                                <div class="in-tech__form__content--input form-group">
                                    <label for="exampleInputEmail1">Nome da amiga</label>
                                    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
                                </div>
                                <div class="in-tech__form__content--input form-group">
                                    <label for="exampleInputEmail1">Qual o e-mail da sua amiga?</label>
                                    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
                                </div>
                                <div class="in-tech__form__content--input form-group">
                                    <label for="exampleInputEmail1">Qual o seu nome?</label>
                                    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
                                </div>

                                <div class="in-tech__form__content--btn">
                                    <a class="popin-btn" type="button" data-toggle="modal" data-target="#firstvideo">
                                        <button class="in-tech__btn btn" type="button" data-toggle="modal" data-target="#indique">Enviar</button>
                                    </a>
                                </div>
                                
                            <div class="modal fade" id="indique" tabindex="-1" role="dialog" aria-labelledby="indiqueTitle" aria-hidden="true">
                                <div class="modal-dialog modal-dialog-centered" role="document">
                                <div class="modal-content">
                                    <div class="modal-body">
                                        Obrigada por indicar uma amiga! Logo logo entraremos em contato! ;D
                                    </div>
                                </div>
                                </div>
                            </div>
                            </form>
                
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>

.in-tech__form__content.indique {
    margin-top: 2rem;
}
.in-tech__form__content {
    padding: 0;
}

.in-tech__banner {
    margin: 2rem 4rem;
}

.in-tech__banner  img {
    width: 100%;
    border-radius: 10px;
}
</style>