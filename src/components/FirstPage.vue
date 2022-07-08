<template>
    <div>
        <div class="container first-element" v-if="step == 1">
            <div class="form-main-wraper">
                <h1>Sobre o profissional</h1>
                <h2>Dados do profissional</h2>
                <b-form class="form-step-1">
                    <b-row>
                        <b-col sm="12" md="12" xs="12">
                            <div class="w-100">
                                <b-form-group
                                    label="Nome completo*"
                                    label-for="nome"
                                >
                                    <b-form-input
                                        required
                                        v-model="form.nome"
                                        id="nome"
                                        placeholder="Digite o nome completo"
                                    ></b-form-input>
                                </b-form-group>
                            </div>
                        </b-col>
                    </b-row>
                    <b-row>
                        <b-col sm="12" md="12" xs="12">
                            <b-form-group label="CPF*" label-for="cpf">
                                <b-form-input
                                    required
                                    v-model="form.cpf"
                                    id="cpf"
                                    placeholder="Digite um CPF"
                                ></b-form-input>
                            </b-form-group>
                        </b-col>
                    </b-row>
                    <b-row>
                        <b-col sm="12" md="12" xs="12">
                            <b-form-group
                                label="Número de celular*"
                                label-for="celular"
                            >
                                <b-form-input
                                    required
                                    v-model="form.celular"
                                    id="celular"
                                    placeholder="(00) 00000-0000"
                                ></b-form-input>
                            </b-form-group>
                        </b-col>
                    </b-row>

                <DropCityState/>

               <ProgressBar page="1 de 2"/>

                    <div class="mt-3 btn-sbmt">
                        <button v-on:click="nextStep, formSubmit" type="submit">
                            Próximo
                        </button>
                    </div>
                </b-form>
            </div>
            <div class="img-form">
                <img :src="img" :alt="alt" class="img-responsive" />
            </div>
        </div>

        <!-- <div class="container second-element" v-if="step == 2">
                <div class="form-main-wraper">
                    <div class="back-arrow">
                        <a v-on:click.prevent="prevStep">
                            <i class="icon-chevron-sign-left"></i>
                        </a>
                    </div>
                    <h1>Sobre o Atendimento</h1>

                    <h2>Detalhes do atendimento</h2>
                    <b-form>
                        <b-row>
                            <b-col sm="12" md="12" xs="12">
                                <b-form-group
                                    label="Nome completo*"
                                    label-for="nome"
                                >
                                    <b-form-input
                                        required
                                        v-model="form.name"
                                        id="nome"
                                        placeholder="Digite o nome completo"
                                    ></b-form-input>
                                </b-form-group>
                            </b-col>
                        </b-row>
                        <b-row>
                            <b-col sm="12" md="12" xs="12">
                                <b-form-group label="CPF*" label-for="cpf">
                                    <b-form-input
                                        required
                                        v-model="form.cpf"
                                        id="cpf"
                                        placeholder="Digite um CPF"
                                    ></b-form-input>
                                </b-form-group>
                            </b-col>
                        </b-row>
                        <b-row>
                            <b-col sm="12" md="12" xs="12">
                                <b-form-group
                                    label="Número de celular*"
                                    label-for="celular"
                                >
                                    <b-form-input
                                        required
                                        v-model="form.celular"
                                        id="celular"
                                        placeholder="(00) 00000-0000"
                                    ></b-form-input>
                                </b-form-group>
                            </b-col>
                        </b-row>
                        <b-row>
                            <b-col sm="6" md="6" xs="6">
                                <b-form-group
                                    id="estado"
                                    label="Estado:"
                                    label-for="estado"
                                >
                                    <b-form-select
                                        v-model="form.estado"
                                        :options="estados"
                                    ></b-form-select>
                                </b-form-group>
                            </b-col>
                            <b-col sm="6" md="6" xs="6">
                                <b-form-group
                                    id="cidade"
                                    label="Cidade:"
                                    label-for="cidade"
                                >
                                    <b-form-select
                                        v-model="form.cidade"
                                        :options="cidades"
                                    ></b-form-select>
                                </b-form-group>
                            </b-col>
                        </b-row>

                    <ProgressBar page="2 de 2"/>

                        <div class="mt-3 btn-sbmt">
                            <button v-on:click="nextStep" type="submit">
                                Próximo
                            </button>
                        </div>
                    </b-form>
                </div>
                <div class="img-form-2">
                    <img :src="img2" :alt="alt2" class="img-responsive" />
                </div>
            </div> -->
    </div>
</template>

<script>
import Vue from "vue";
import { BootstrapVueIcons } from "bootstrap-vue";
import "bootstrap-vue/dist/bootstrap-vue-icons.min.css";
import ProgressBar from "./ProgressBar.vue";
import DropCityState from "./DropCityState.vue";

Vue.use(BootstrapVueIcons);

export default {
  components: { ProgressBar, DropCityState },
    name: "FirstPage",

    data() {
        return {
            img: "/img/desktop-pagina-1.png",
            alt: "desktop img 1",
            img2: "/img/desktop-pagina-2.png",
            alt2: "desktop img 2",
            list: undefined,
            step: 1,
            totalSteps: 3,
            form: {
                nome: null,
                cpf: "",
                estado: "",
                cidade: "",
            },
            estados: [
                { value: null, text: "Selecione uma opção" },
                { value: "RS", text: "Rio Grande do Sul" },
                { value: "SC", text: "Santa Catarina" },
                { value: "PR", text: "Paraná" },
                { value: "GO", text: "Goiás" },
                { value: "MT", text: "Mato Grosso" },
                { value: "MS", text: "Mato Grosso do Sul" },
            ],
            cidades: [
                { value: null, text: "Selecione uma opção" },
                { value: "RS", text: "Pelotas" },
                { value: "SC", text: "Santa Maria" },
                { value: "PR", text: "Joinville" },
                { value: "GO", text: "Caxias do Sul" },
                { value: "MT", text: "Londrina" },
                { value: "MS", text: "Maringá" },
                { value: "MS", text: "Cuiabá" },
                { value: "MS", text: "Goiânia" },
                { value: "MS", text: "Campo Grande" },
                { value: "MS", text: "Florianópolis" },
                { value: "MS", text: "Porto Alegre" },
            ],
        };
    },
    mounted() {},
    methods: {
        onSubmit(event) {
            event.preventDefault();
            alert(JSON.stringify(this.form));
        },
        onReset(event) {
            event.preventDefault();
            // Reset our form values
            this.form.email = "";
            this.form.name = "";
            this.form.checked = [];
            // Trick to reset/clear native browser form validation state
            this.show = false;
            this.$nextTick(() => {
                this.show = true;
            });
        },
        saveFile(event) {
            console.log(event);
        },

        nextStep: function () {
            this.step++;
        },

        prevStep: function () {
            this.step--;
        },
    },
};
</script>

<style>
.first-element,
.second-element,
.third-element {
    display: flex;
    background-color: #fff;
    border-radius: 20px;
    padding: 60px;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: center;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}

.form-main-wraper {
    padding: 10px 20px;
    text-align: left;
}

.form-main-wraper input {
    width: 70%;
    padding: 16px;
    border: 1px solid #483698;
    margin-bottom: 40px;
}

.w-100 input {
    width: 100% !important;
}

.btn-sbmt button {
    width: 100%;
    background-color: #483698;
    text-align: center;
    color: #fff;
    border-radius: 10px;
    border: 0;
    font-size: 20px;
    padding: 3px;
    text-transform: uppercase;
}
.pg-wrap {
    display: flex;
    align-content: center;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
}
.pg-wrap p {
    font-family: "Comfortaa", cursive;
    margin: 20px;
    font-size: 1.2em;
    color: #483698;
    font-weight: 800;
}
</style>
