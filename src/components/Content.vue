<template>
    <b-container class="bv-example-row p-5">
        <b-row v-for="(d, i) in translated" :key="d.url" class="py-5">
                
                <p>{{d.url}}</p>
                <b-img :src="d.url" class="myFlex data-img myWidth" @mouseover="mouseOver(i)" @mouseout="mouseLeave(i)"></b-img>
                <div class="abolute-pos myWidth ">
                    <p class="data-text myFlex " >
                        {{d.translation}}  
                    </p> 
                </div>
          
        </b-row>
    </b-container>
</template>

<script>
import axios from '../../config/axios'

export default {
    data(){
        return {
            translated: [],
            imageUrl: ''
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
        },
        mouseOver: function(i) {
            let text = document.getElementsByClassName('data-text')[i];
            text.style.color = 'black';
        },
        mouseLeave: function(i) {
            let text = document.getElementsByClassName('data-text')[i];
            text.style.color = 'transparent';
        }
    },
    created() {
        this.fetchTranslatedData()
    },
    fetchUrl(url) {
        this.u
    }
}


</script>

<style>
    .data-img {
        transition: all .4s ease-in-out;
    }
    .data-img:hover {
        opacity: 0.1;
        transform: scale(1.2);
    }

    .data-text {
        color: transparent;
        position: absolute;
        top: 50%;
        width: 400px;
        margin-left: -200px;
        left: 50%;
        text-align: center;
        font-size: 14px;
    }

    .myWidth{
        /* width: 700px;
        height: auto; */
        width: 500px;
        height: 500px;
        object-fit: contain;
    }

    .abolute-pos {
        position: absolute;
        width: 700px;
    }

    .myFlex{
        margin: 0 auto;
    }
    
</style>