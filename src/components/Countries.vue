<template>
    <div>
        <div class="row text-center">
            <div class="col jumbotron">
                <h2 class="mb-5">Select an option to show countries information</h2>
                <button class="btn btn-outline-success mr-5" @click="selectedComponent = 'all-countries'">All countries</button>
                <button class="btn btn-outline-success" @click="selectedComponent = 'specific-country'">Custom search</button>
            </div>
        </div>
        <component :is="selectedComponent"></component>
    </div>

</template>

<script>
    import AllCountries from '@/components/AllCountries'
    import SpecificCountry from '@/components/SpecificCountry'

    export default {
        name: "Countries",
        components: {
            'all-countries': AllCountries,
            'specific-country': SpecificCountry
        },
        data (){
            return {
                selectedComponent: ''
            }
        }
    }
</script>

<style scoped>

</style>
