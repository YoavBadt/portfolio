<template >
    <main class="">
        
        <ContentDoc v-slot="{ doc }">
            <div class="main_1 ">
                <div class="label">project name:</div>
                <h1 class="main_1_h1">{{ doc.name }}</h1>
                <div class="label">description:</div>
                <p class="main_1_desc">{{ doc.description }}</p>
                <div class="label">about the project:</div>
                <ContentRendererMarkdown class="main_1_p" :value="doc" />
            </div>

            <div class="main_2 ">
              
                <template v-if="doc.iframe">
                    <div class="main_2_iframe" :style="{backgroundImage : `url(${doc.iframeAlt})`}">
                        <iframe  style="width:100%;height:100%" frameborder="0" :src="doc.iframe" ></iframe>
                    </div>
                </template>
                
                <template v-if="doc.images">

                    <div class="main_2_img_box" v-for="image in doc.images">
                        <!-- <img class="main_2_img" :src="image"/> -->
                        <NuxtImg class="main_2_img" :src="image" preload />
                    </div>
                </template>

            </div>
        </ContentDoc>
        
   </main>
</template>
<script>
    import Mygrid from './components/mygrid/mygrid.vue'
    export default {
        data(){
            return{
                iframeOK : false
            }
        },
        methods:{
            iframeLoaded(){
                this.iframeOK = true;
            
            }
        }
    }
</script>
<style >
    .label{
        /* color:rgba(0,0,0,0.5); */
        text-transform: capitalize;
        font-size:12px;
        line-height:20px;
        /* margin-bottom:5px; */
        font-weight: 300;
    }
    .main_1_h1{
        line-height:40px;
        margin-bottom: 40px;
        /* font-size: 10cqw; */
    }
    .main_1_desc{
        font-weight: 600;
        margin-bottom:40px;
    }
    .main_1_p p{
        font-weight: 400;
        margin-bottom:20px;
    }
    .main_1_p p a{
        /* color: #E44B2B; */
        color:#11a8ff;
        /* border-bottom:1px solid #11a8ff; */
        font-weight: 400;
        margin-bottom:20px;
    }
    .main_2_img_box{
        flex-grow: 0;
        width:calc(33% - 40px);
        max-height: 90vh;
        /* height:100%; */
        overflow: hidden;
        /* background:Red; */
        /* margin-bottom:40px; */
    }
    .main_2_img_box:nth-child(3n){
        margin-right:-40px;
    }
    .main_2_img{
        width:100%;
        height:100%;
        object-fit: cover;
        object-position: 50% 0%;
        border-radius: 5px;
        overflow: hidden;
        /* border:1px dotted #8A837C; */
        /* width:100%; */

    }
    .main_2_iframe{
        width:100%;
        height:100%;
        border-radius:10px;
        overflow:hidden;
        background:lightgrey;
        background-repeat: none;
        background-size: 100% 100%;
    }
</style>