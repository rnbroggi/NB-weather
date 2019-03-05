<template>
    <div id="app">
        <my-header
                @changeToCountries="selectedMainComponent = $event"
                @changeToHome="selectedMainComponent = $event"
                @changeToWeather="selectedMainComponent = $event"
        >

        </my-header>
        <div class="container">
            <div class="jumbotron" v-if="selectedMainComponent === ''">
                <h1 class="mb-5">Welcome to NB Weather!</h1>
                <h2 class="mb-4">Click if you want to look for <button class="btn btn-success" @click="selectedMainComponent = 'countries'">Countries</button></h2>
                <h2>Click if you want to look for <button class="btn btn-info" @click="selectedMainComponent = 'weather'">Weather</button></h2>
            </div>
            <component :is="selectedMainComponent"></component>
        </div>
    </div>
</template>

<script>
    import Countries from '@/components/Countries'
    import myHeader from '@/components/Header'
    import Weather from '@/components/Weather'

    export default {
        /* eslint-disable */

        name: 'app',
        components: {
            myHeader,
            'countries': Countries,
            'weather': Weather
        },
        data (){
            return {
                selectedMainComponent: ''
            }
        }
    }
</script>

<style>
    body {
        background-color: #efefef;
    }
</style>
