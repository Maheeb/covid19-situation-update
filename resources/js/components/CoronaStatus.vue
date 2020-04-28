<template>
    <div class="container">
            <!--<h1>Hello world</h1>-->
        <!--<select name="country">-->
            <!--<option  value="">Choose</option>-->
            <!--&lt;!&ndash;<option v-for="country in countryList" :key="country" :value="country">&ndash;&gt;-->
                <!--&lt;!&ndash;{{ country }}&ndash;&gt;-->
            <!--&lt;!&ndash;</option>&ndash;&gt;-->
            <!--<option v-for="(item,index) in countryList" :key="item.id" :index="index">-->
                <!--{{ item }}-->
            <!--</option>-->

        <!--</select>-->


        <div class="p-3 mb-2 bg-info text-white text-center text-uppercase" style="font-size: 20px">Worldwide Update</div>
        <div class="row">

            <div class="col-md-4">
                <div class="card text-white bg-dark mb-3" style="max-width: 18rem;">
                    <div class="card-body">
                        <h5 class="card-title text-center">Total Confirmed</h5>
                        <p class="card-text text-center font-weight-bold" style="font-size: 30px">{{totalConfirmed}}</p>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="card text-white bg-success mb-3" style="max-width: 18rem;">
                    <div class="card-body">
                        <h5 class="card-title text-center">Total Recovered</h5>
                        <p class="card-text text-center font-weight-bold" style="font-size: 30px">{{totalRecovered}}</p>
                    </div>
                </div>

            </div>
            <div class="col-md-4">
                <div class="card text-white bg-danger mb-3" style="max-width: 18rem;">
                    <div class="card-body">
                        <h5 class="card-title text-center">Total Death</h5>
                        <p class="card-text text-center font-weight-bold" style="font-size: 30px">{{totalDeath}}</p>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        data: function () {
            return {
                Recovered: "Loading ...",
                countryList: [],
                totalConfirmed: '',
                totalRecovered: '',
                totalDeath: '',
            }
        },
        mounted() {
            this.globalStatus()
        },
        methods: {
            // countryStatus () {
            //     const options = {
            //         headers: 	{
            //             "x-rapidapi-host": "covid-193.p.rapidapi.com",
            //             "x-rapidapi-key": "ad21211fe4mshba485cda44108adp1712e0jsn54ed45914a9a"
            //         }
            //     }
            //     axios.get('https://covid-193.p.rapidapi.com/countries', options).then(res => {
            //         this.countryList = res.data.response
            //         console.log(this.countryList);
            //     })
            // },

            globalStatus: function () {

                axios.get('https://api.covid19api.com/summary')

                    .then((response) => {
                        // this.recovered = response.data.Global.NewConfirmed;
                        this.totalConfirmed = response.data.Global.TotalConfirmed;
                        this.totalRecovered = response.data.Global.TotalRecovered;
                        this.totalDeath = response.data.Global.TotalDeaths;

                        // document.getElementById('test_5').innerHTML = "total: " + this.TotalRecovered;

                    }).catch(err => console.log(err));


            },


        }
    }
</script>

<style scoped>

</style>