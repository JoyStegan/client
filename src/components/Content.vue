<template>
    <b-container class="bv-example-row p-5">
        <h3 class="text-center">Feed</h3>
        <b-row v-for="d in translated" :key="d.data.url" class="py-5">
            <b-col>
                <b-img :src="d.data.url"  class="data-img abolute-pos"></b-img>
                <div class="abolute-pos">
                    <p class="data-text">
                        {{d.data.translation}}  
                    </p> 
                </div>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
import axios from '../../config/axios'

export default {
    data(){
        return {
            translated: []
        };
    },
    methods: {
        fetchTranslatedData: function() {
            axios({
                method: "GET",
                url: "/translations"
            })
            .then(({data}) => {
                this.translated = data;
            })
            .catch( err => {
                console.log(err)
            })
        }
    },
    created() {
        this.fetchTranslatedData()
    }
}
</script>

<style>
    .data-img {
        transition: all .4s ease-in-out;
    }
    .data-img:hover {
        opacity: 0.2;
        transform: scale(1.2);
    }

    .data-text {
        position: absolute;
        top: 100px;
        z-index: 2;
        width: 400px;
        margin-left: -200px;
        left: 50%;
        text-align: center;
        line-height: 1.6;
        font-size: 18px;
    }

    .abolute-pos {
        position: absolute;
        width: 700px;
    }
    
</style>