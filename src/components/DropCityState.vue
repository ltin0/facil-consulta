<template>
    <div>
        {{ stateSelected }}
        
        <b-row>
            <b-col sm="6" md="6" xs="6">
                <b-form-group id="estado" required label="Estado:" label-for="estado">
                    <b-form-select>
                        <option
                            v-for="estado in estados"
                            :key="estado.id"
                            @click="selectState(estado)"
                        >
                            {{ estado.nome }}
                        </option>
                    </b-form-select>
                </b-form-group>
            </b-col>
            <b-col sm="6" md="6" xs="6">
                <b-form-group id="cidade" label="Cidade:" label-for="cidade">
                    <b-form-select>
                        <option
                            v-for="cidade in cidades"
                            :key="cidade.id"
                            @click="selectState(cidade)"
                        >
                            {{ cidade.nome }}
                        </option>
                    </b-form-select>
                </b-form-group>
            </b-col>
        </b-row>
    </div>
</template>

<script>
export default {
    name: "DropCityState",
    data() {
        return {
            form: {
                estado: "",
                cidade: "",
            },
            estados: [],
            cidades: [],
            stateSelected: [],
        };
    },

    created() {
        this.getStates();
    },

    methods: {
        getStates() {
            fetch("https://api-teste-front-end-fc.herokuapp.com/estados")
                .then((response) => response.json())
                .then((data) => {
                    this.estados = data;
                });
        },

        getCities(){
                fetch("https://api-teste-front-end-fc.herokuapp.com/cidades")
                .then((response) => response.json())
                .then((data) => {
                    this.cidades = data;
                });
        },

        selectState(estado){
            
            this.stateSelected = estado;

            console.log(estado);
        }
    },
};
</script>

<style></style>
