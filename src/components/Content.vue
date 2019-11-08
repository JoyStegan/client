<template>
    <b-container class="bv-example-row p-5">
        <b-row v-for="(d, i) in translated" :key="d.url" class="py-5">
            <b-img :src="d.url" class="myFlex data-img myWidth" @mouseover="mouseOver(i)" @mouseout="mouseLeave(i)"></b-img>
            <div class="abolute-pos myWidth ">
                <p class="data-text myFlex " >
                    {{d.translation}}  
                </p> 
            </div>
            <div id="share-btns">
                <div data-network="twitter" :data-title="d.translation" :data-url="d.url" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:#1A91DA; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 22px;
                    color: white;
                    border-radius: 4px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    margin: 4px" 
                    type="button" class="btn share-btn"><i class="fab fa-twitter share-icon"></i></button>
                </div>

                <div data-network="facebook" :data-title="d.translation" :data-url="d.url" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:#4267B2; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 22px;
                    color: white;
                    border-radius: 4px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    margin: 4px" 
                    type="button" class="btn share-btn"><i class="fab fa-facebook-square"></i></button>
                </div>
                
                <div data-network="pinterest" :data-title="d.translation" :data-url="d.url" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:#CB2027; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 22px;
                    color: white;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border-radius: 4px;
                    margin: 4px"
                    type="button" class="btn share-btn"><i class="fab fa-pinterest"></i></button>
                </div>

                <div data-network="line" :data-title="d.translation" :data-url="d.url" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:#42C607; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 25px;
                    color: white;
                    border-radius: 4px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border:1px solid white;
                    margin: 4px" 
                    type="button" class="btn share-btn"><i class="fab fa-line"></i></button>
                </div>

                <div data-network="gmail" :data-title="d.translation" :data-url="d.url" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:#FFFFFF; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 22px;
                    color: black;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border-radius: 4px;
                    border:1px solid black;
                    margin: 4px" 
                    type="button" class="btn share-btn"><i class="fab fa-google"></i></button>
                </div>

                <div data-network="whatsapp" data-title="Denko Sekka" :data-url="d.url" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:#2AB200; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 25px;
                    color: white;
                    border-radius: 4px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border:1px solid white;
                    margin: 4px" 
                    type="button" class="btn share-btn"><i class="fab fa-whatsapp"></i></button>
                </div>

                <div data-network="linkedin" data-title="Denko Sekka" :data-url="d.url" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:#0173B2; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 25px;
                    color: white;
                    border-radius: 4px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border:1px solid white;
                    margin: 4px" 
                    type="button" class="btn share-btn"><i class="fab fa-linkedin-in"></i></button>
                </div>

                <div data-network="flipboard" data-title="Denko Sekka" :data-url="d.url" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:#E32828; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 25px;
                    color: white;
                    border-radius: 4px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border:1px solid white;
                    margin: 4px" 
                    type="button" class="btn share-btn"><i class="fab fa-flipboard"></i></button>
                </div>

                <div data-network="reddit" data-title="Denko Sekka" :data-url="d.url" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:#FF4500; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 25px;
                    color: white;
                    border-radius: 4px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border:1px solid white;
                    margin: 4px" 
                    type="button" class="btn share-btn"><i class="fab fa-reddit"></i></button>
                </div>

                <div data-network="print" class="st-custom-button">
                    <button  
                    style="cursor: pointer; 
                    background-color:gray; 
                    height: 45px; 
                    width: 50px; 
                    font-size: 25px;
                    color: white;
                    border-radius: 4px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border:1px solid white;
                    margin: 4px" 
                    type="button" class="btn share-btn"><i class="fas fa-print"></i></button>
                </div>
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