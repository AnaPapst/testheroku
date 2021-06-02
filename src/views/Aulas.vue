<template>
    <div class="in-tech__banner-course">
        <div class="in-tech__course">
            <p class="in-tech__course__header--top">HTML</p>
            <b-container fluid="sm">
                <b-row>
                    <b-col class="in-tech__img">
                        <b-button v-b-modal.modal-1>
                            <img src="../images/thumbnail_html.png">
                        </b-button>
                        <b-modal id="modal-1" title="Introdução">
                            <iframe width="560" height="315" src="https://youtu.be/h0VhHkekmOY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                            <b-form-checkbox switch size="lg">Eu assisti</b-form-checkbox>
                        </b-modal>
                        <span>Aula I</span>
                    </b-col>
                    <b-col class="in-tech__img">
                        <b-button v-b-modal.modal-2>
                            <img src="../images/thumbnail2_html.png">
                        </b-button>
                        <b-modal id="modal-2" title="Primeiro componente">
                            <iframe width="560" height="315" src="https://youtu.be/5Wgo3raLvRE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                        </b-modal>
                        <span>Aula II</span>
                    </b-col>
                    <b-col class="in-tech__img">
                        <b-button v-b-modal.modal-4>
                            <img src="../images/thumbnail3_html.png">
                        </b-button>
                        <b-modal id="modal-4" title="Introdução">
                            <iframe width="560" height="315" src="https://youtu.be/DXI-Tr-u3Hc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                        </b-modal>
                        <span>Aula III</span>
                    </b-col>
                </b-row>
                <div class="in-tech__rating">
                    <b-form-rating v-model="value" readonly show-value precision="2"></b-form-rating>
                </div>
            </b-container>
        </div>

        <div class="in-tech__course">
            <p class="b-top in-tech__course__header">CSS</p>
            <b-container fluid="lg">
                <b-row>
                    <b-col class="in-tech__img">
                        <b-button v-b-modal.modal-4>
                            <img src="../images/thumbnail3_html.png">
                        </b-button>
                        <b-modal id="modal-4" title="Introdução">
                            <iframe width="560" height="315" src="https://youtu.be/DXI-Tr-u3Hc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                        </b-modal>
                        <span>Introdução</span>
                    </b-col>
                    <b-col class="in-tech__img">
                        <b-button v-b-modal.modal-5>
                            <img src="../images/thumbnail4_html.png">
                        </b-button>
                        <b-modal id="modal-5" title="Primeiro componente">
                            <iframe width="560" height="315" src="https://youtu.be/gxH2d_sufvA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                        </b-modal>
                        <span>Primeiro componente</span>
                    </b-col>
                </b-row> 
                <div class="in-tech__rating">
                    <b-form-rating v-model="value" readonly show-value precision="2"></b-form-rating>
                </div>   
            </b-container>
        </div>
        <router-link to="/envioProjeto" class="nav-link">
            <span class="in-tech__nav-btn send light">Envie seu projeto</span>
        </router-link>
        
    </div>
</template>


<script>
import UserService from '../services/user.service';

export default {
  name: 'User',
  data() {
    return {
      content: '',
      value: 3.555
    };
  },
  mounted() {
    UserService.getUserBoard().then(
      response => {
        this.content = response.data;
      },
      error => {
        this.content =
          (error.response && error.response.data) ||
          error.message ||
          error.toString();
      }
    );
  }
};
</script>

<style>
.btn {
    border-radius: 15px;
}

.btn-primary {
    background-color: #caf7e3;
    border: none;
    color: grey;
}

.btn-primary:hover {
    color: #fff !important;
    background-color: #5f939a !important;
    border-color: #5f939a !important;
}

.in-tech__banner-course {
    margin: 1rem;
    border: 3px solid black;
    border-radius: 20px;
}

.in-tech__course {
    margin-bottom: 15px;
}

.b-top {
    border-top: 2px solid black;
}

.in-tech__course p {
    width: 100%;
    padding: .5rem 0 .5rem 1rem;
    text-transform: uppercase;
    border-bottom: 1px solid  black;
    font-weight: bold;
}

.in-tech__img {
    text-align: center;
}

.in-tech__img img {
    width: 100%;
}

.in-tech__img span {
    display: block;
    margin-top: .5rem;
}

.in-tech__img popin-btn {
    cursor: pointer;
}

iframe {
    width: 100%;
}

.in-tech__course__header {
    background-color: #caf7e3;
}

.in-tech__course__header--top {
    background-color: #caf7e3;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
}

.custom-control-label {
    text-transform: uppercase;
}

.in-tech__nav-btn.send {
    display: block;
    margin: 2rem;
    text-align: center;
    color: black;
}

.in-tech__rating {
    margin: 1rem;
}

@media (min-width:720px) {
    .in-tech__banner-course {
        margin: 3rem;
    }
}
</style>