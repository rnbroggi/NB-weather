<template>
    <div>
        <div class="row justify-content-center text-center">
            <div class="col-lg-4">
                <h3 class="mb-3">Enter a country name:</h3>
                <div class="input-group">
                    <input @keyup="fetchData" v-model="country" class="form-control width100">
                    <span class="input-group-btn">
        <button class="btn btn-info" @click="fetchData">Search</button>
    </span>
                </div>
            </div>
        </div>

        <table class="table table-striped table-dark mt-5" v-if="country != ''">
            <thead>
            <tr class="main-tr">
                <th scope="col">Country</th>
                <th scope="col">Capital</th>
                <th scope="col">Region</th>
                <th scope="col">Subregion</th>
                <th scope="col">Population</th>
                <th scope="col">Calling code</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="country in allCountries">
                <td>{{country.name}}</td>
                <td>{{country.capital}}</td>
                <td>{{country.region}}</td>
                <td>{{country.subregion}}</td>
                <td>{{country.population}}</td>
                <td>{{country.callingCodes}}</td>
            </tr>
            </tbody>
        </table>

    </div>
</template>

<script>
    export default {
        name: "SpecificCountry",
        data() {
            return {
                country: '',
                allCountries: '',
                allCountriesNames: []
            }
        },
        methods: {
            fetchData() {
                /* eslint-disable no-console */
                console.log(this.text);
                this.$http.get('https://restcountries.eu/rest/v2/name/' + this.country)
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
                                population: data[key].population,
                                subregion: data[key].subregion,
                                callingCodes: data[key].callingCodes.join(', ')
                            };
                            resultArray.push(country)
                        }
                        this.allCountries = resultArray;
                    })
            }
        },
    }
</script>

<style scoped>

</style>
