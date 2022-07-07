<template>
    <div>
        <section class="fondoceleste">
            <h1>Random Gif Cat</h1>
        </section>

        <section class="fondorosado">
            <!--Titulo-->
            <div class="espacio">
                <label>Titulo:</label>
                <input type="text" v-model="titulo">
            </div>
            <!--Filtro-->
            <div class="espacio">
                <label>Filtro:</label>
                <select @change="changeFiltro">
                    <option v-for="filtro in filtros" :key="filtro" :value="filtro">
                        {{ filtro }}
                    </option>
                </select>
            </div>
            <!--Colores-->
            <div class="espacio">
                <label>Color:</label>
                <select @change="changeColor">
                    <option v-for="color in colores" :key="color.value" :value="color.value">
                        {{ color.color }}
                    </option>
                </select>
                <div class="circulo" :style="{ backgroundColor: this.color }"></div>
            </div>
            <!--Tamaño-->
            <div>
                <label>Tamaño:</label>
                <input type="number" v-model="tamaño">
            </div>
        </section>
        <section class="fondoceleste">
            <button @click="fetchGato">
                Obtener mi gatito
            </button>
            <img :src="gif" alt="">

        </section>
    </div>

</template>

<script>
export default {
    name: 'component-name',
    // props: {},
    data: function () {
        return {

            titulo: 'Miau',
            filtro: 'blur',
            color: 'blue',
            tamaño: 30,
            gif: '',

            filtros: [
                'blur',
                'mono',
                'sepia',
                'negative',
                'paint',
                'pixel'
            ],

            colores: [
                {
                    color: "Azul",
                    value: "blue"
                },
                {
                    color: "Rojo",
                    value: "red"
                },
                {
                    color: "Verde",
                    value: "green"
                },
                {
                    color: 'Blanco',
                    value: 'white'
                },
                {
                    color: 'Amarillo',
                    value: 'yellow'
                }
            ],
        }
    },
    computed: {

    },
    methods: {
        async fetchGato() {
            try {
                let data = await fetch(`https://cataas.com/cat/gif/says/${this.titulo}?filter=${this.filtro}&color=${this.color}&size=${this.tamaño}`)
                if (!data.ok) throw ('Error en petición')

                this.gif = data.url

            }
            catch (error) {
                console.log(error)
            }
        },

        changeFiltro(event) {
            this.filtro = event.target.value
        },

        changeColor(event) {
            this.color = event.target.value
        },



        // -- UI Modification
        // -- Data fetching
        // -- Data handling and transformations
        // -- Validations and Error handling
        // -- Other functions
        // -- Vuex mappings
    },
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
.fondoceleste {
    background-color: lightblue;
    padding: 10px;
    font-size: 30px;
}

.fondorosado {
    background-color: lightcoral;
    padding: 10px 0px;
}

.espacio {
    padding-bottom: 10px;
}

.circulo {
    width: 20px;
    height: 20px;
    display: inline-block;
    border-radius: 50%;
    margin-left: 10px;
}

img {
    display: block;
    margin: auto;
    padding-top: 10px;
}
</style>