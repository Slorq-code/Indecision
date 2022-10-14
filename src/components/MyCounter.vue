
<template>
    <h2>{{customTitle}}</h2>
    <p> {{counter}} <sup>2</sup> = {{squareCounter}} </p>

    <div>
        <button @click="increase">+1</button>
        <button @click="decrease">-1</button>
    </div>

</template>

<script>

export default {
    props: {
        title: String,
        start: {
            type: Number,
            // required: true
            validator (value) {
                return value ? value >= 0 : "Debe ser positivo"
            },
        }
    },
    data() {
        return {
            counter: 2,
        }
    },
    methods: {
        getSquareValue() {
            this.counter * this.counter
        },
        increase () {
            this.counter++
        },
        decrease () {
            this.counter--
        }
    },
    computed: {
        squareCounter() {
            return this.counter * this.counter
        },
        customTitle() {
            return this.title ? this.title : "Counter"
        }
    }
}

</script>

<style>
    button {
        background-color: #2ed357;
        border-radius: 5px;
        border: 1px solid white;
        color: white;
        cursor: pointer;
        margin: 0 5px;
        padding: 5px 15px;
        transition : 0.3s ease-in-out;
    }

    button:hover {
        background-color:#2a573d ;
        transition : 0.3s ease-in-out;
    }

</style>