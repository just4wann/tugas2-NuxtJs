<script>
    export default {
        data() {
            return {
                display: false
            }
        },
        methods: {
            isAveraging() {
                this.display = true
            },
            isClear() {
                this.display = false
            }
        },
        props: {
            average: String
        },
        emits: ['count', 'clear']
    }
</script>

<template>
    <section class="avg">
        <h4>Rata-Rata Nilai : {{ average }}</h4>
        <div class="btn">
            <button class="btn-avg" @click="$emit('count'), isAveraging()">Hitung Rata-Rata</button>
            <button class="btn-clear" v-if="display" @click="$emit('clear'), isClear()">Reset</button>
        </div>
    </section>
</template>