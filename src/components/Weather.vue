<template>
    <div>
        <h1 class="text-center">Current weather in Buenos Aires, Argentina</h1>
        <div class="jumbotron">
            <div class="row">
                <div class="col text-center winfo">
                    <h1 class="mt-3">Current temperature: {{currentTemp}} °C</h1>
                    <h1 class="mb-4">{{overcast}}</h1>
                </div>

            </div>
            <div class="row justify-content-center">
                <div class="col-lg-4 col-sm-12 text-center mt-5 winfo">
                    <h2>Min: {{minTemp}} °C</h2>
                    <h2>Max: {{maxTemp}} °C</h2>
                    <h2>Pressure: {{pressure}} hpa</h2>
                    <h2>Humidity: {{humidity}}</h2>
                    <h2>Wind: {{wind}}</h2>
                </div>
            </div>
            <p>Provided by https://openweathermap.org/</p>
        </div>


    </div>
</template>

<script>
    export default {
        name: "weather",
        data() {
            return {
                currentTemp: '',
                minTemp: '',
                maxTemp: '',
                pressure: '',
                humidity: '',
                wind: '',
                overcast: '',
            }
        },
        methods: {
            fetchWeatherData() {
                /* eslint-disable no-console */
                console.log(this.text);
                this.$http.get("https://api.openweathermap.org/data/2.5/weather?id=3435910&units=metric&appid=8f96651fbea9504a7ef6fb781526e8cc")
                    .then(response => {
                        return response.json()
                    })
                    .then(data => {
                        this.currentTemp = data.main.temp.toFixed(1);
                        this.minTemp = data.main.temp_min.toFixed(1);
                        this.maxTemp = data.main.temp_max.toFixed(1);
                        this.pressure = data.main.pressure;
                        this.humidity = data.main.humidity + '%';
                        this.wind = data.wind.speed + 'm/s';
                        this.overcast = data.weather[0].description.replace(/\b[a-z]/g, match => match.toUpperCase());
                    })
            }
        },
        created() {
            this.fetchWeatherData()
        }
    }
</script>

<style scoped>

    p {
        font-style: italic;
        text-align: center;
        margin-top: 30px;
        color: grey;
    }

    .winfo {
        border: 3px solid darkblue;
        -webkit-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.47);
        -moz-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.47);
        box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.47);
    }
</style>
