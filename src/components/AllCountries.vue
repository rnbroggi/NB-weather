<template>
    <div class="mt-5">
        <table class="table table-striped table-dark">
            <thead>
            <tr class="main-tr">
                <th scope="col">Country</th>
                <th scope="col">Capital</th>
                <th scope="col">Region</th>
                <th scope="col">Population</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="country in allCountries">
                <td>{{country.name}}</td>
                <td>{{country.capital}}</td>
                <td>{{country.region}}</td>
                <td>{{country.population}}</td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default {
        name: "AllCountries",
        data() {
            return {
                city: '',
                allCountries: [],
                filterCountries: ''
            }
        },
        methods: {
            fetchData() {
                /* eslint-disable no-console */
                console.log(this.text);
                this.$http.get('https://restcountries.eu/rest/v2/all')
                    .then(response => {
                        return response.json()
                    })
                    .then(data => {
                        const resultArray = [];
                        for (let key in data) {
                            const country = {
                                name: data[key].name,
                                capital: data[key].capital,
                                region: data[key].region,
                                population: data[key].population
                            };
                            resultArray.push(country)
                        }
                        this.allCountries = resultArray;
                    })
            },
        },
        created() {
            this.fetchData();
        }
    }

</script>

<style scoped>
th{
    font-size: 18px;
    font-weight: bold;
    color: orange;
    padding-top: 15px;
    padding-bottom: 15px;
}

.main-tr{
        border-bottom: 5px solid black;
    }
</style>
