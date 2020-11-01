<template>
    <div>
        <h1>{{ header }}</h1>
        <div class="row" >
            <div class="col-sm-6">
                <!-- niet slim -->
                <ul class="list-group">
                    <li class="list-group-item">
                        <span :id="data.countries[0].id"
                              :title="data.countries[0].details">
                            {{data.countries[0].name}} - {{data.countries[0].capital}} - {{data.countries[0].cost}}
                        </span>
                    </li>

                    <li class="list-group-item">
                        <span :id="data.countries[1].id"
                              :title="data.countries[1].details">
                            {{data.countries[1].name}} - {{data.countries[1].capital}}
                        </span>
                    </li>


                </ul>
                <br>
                <!-- wel slim -->
                <ul class="list-group">
                    <li class="list-group-item" v-for="country in data.countries" :key="country.id" @click="details(country.name)" @mouseover="logging(country.cost)">
                        <span :id="country.id"
                              :title="country.details">
                            {{country.name}} - {{country.capital}}
                        </span>
                    </li>
                </ul>
             </div>

        </div>
        {{footer}}
        <br>
        <br>
        {{todo}}
        <span v-html="todo"></span>
        <span v-text="todo"></span> <br>
        <button :disabled="isDisabled" class="btn btn-success">knop opdracht vier</button>
        <button @click="zichtbaar()" class="btn btn-success">toggle</button> <br>

        <select name="list1" id="list1">
            <option v-for="(item, key) in numbers" :value="item" :key="key">
                {{item}}
            </option>
        </select>

    </div>

</template>

<script>
    import countryData from '../data/countryData';
    export default {
        name: "Countries",
        data() {
            return {
                data:countryData,
                header: "Countries",
                footer: "footer",
                todo: '<h2>Clean kitchen</h2>',
                isDisabled:false,
                numbers:[10,20,30,40,50],
            }
        },
        methods: {
                zichtbaar(){
                    if(this.isDisabled===true)
                    {
                        this.isDisabled=false;
                    } else {
                        this.isDisabled=true;
                    }
                },
                details(c)
                {
                    window.alert(c);
                },
                logging(c)
                {
                    console.log(c);
                }

            }
    }
</script>

<style scoped>

</style>