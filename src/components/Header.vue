<template>
    <div class="container mb-5">
        <nav class="navbar navbar-expand navbar-dark bg-primary">
                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav">
                        <li class="nav-item active">
                            <a class="nav-link" href="#" @click="changeToHome">Home</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link active" href="#" @click="changeToWeather">Weather</a>
                        </li>
                        <li class="nav-item active">
                            <a class="nav-link" href="#" @click="changeToCountries">Countries</a>
                        </li>
                    </ul>
                </div>
        </nav>
    </div>
</template>

<script>
    export default {
        name: "myHeader",
        data(){
            return{
                selectedMainComponent: ''
            }
        },
        methods: {
            changeToCountries() {
                this.selectedMainComponent = 'countries';
                this.$emit('changeToCountries', this.selectedMainComponent)
            },
            changeToHome() {
                this.selectedMainComponent = '';
                this.$emit('changeToHome', this.selectedMainComponent)
            },
            changeToWeather() {
                this.selectedMainComponent = 'weather';
                this.$emit('changeToWeather', this.selectedMainComponent)
            }
        }
    }
</script>

<style scoped>

</style>
