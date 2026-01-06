<template lang="">
    <div class="Astro_Div">
        {{ moon }}
        <svg class="top_SVG" xmlns="http://www.w3.org/2000/svg"
        width="100%"
        height="100%"
        
        >
        <rect x="0" y="0" width="100%" height="100%"  fill="darkblue" />
        <circle cx="50%" cy="50%" r="1%" fill="white"/>
        <g>
            <circle cx="50%" cy="50%" r="10%" fill="none" stroke="white"/>

             <!-- <circle cx="getangle.x" cy="getangle.y" r="1%" fill="red"/> -->

            <circle :cx="getangle" :cy="getangle" r="1%" fill="red"/>
        </g>
        </svg>
        <button @click="getangle">angle {{getangle.x}}</button>
    </div>
</template>
<script>
import {createTimeOfInterest} from 'astronomy-bundle/time';
import {createMoon} from 'astronomy-bundle/moon';

export default {
    data(){
        return {
            now: new Date(),
            toi : null,
            jd: null,
            moon : null,

        }
    },
    computed : {
        getangle2(){
            
        //    let rA = this.moon.rightAscension 
        //    let obj = {
        //         x : 250 + 10 * Math.cos(rA * Math.PI / 180),
        //         y : 250 + 10 * Math.sin(rA * Math.PI / 180)
        //    }

        //    console.log(obj)


        //    return obj 
        }
    },
    methods : {
        getangle(){
            let rA = this.moon.rightAscension

            let obj = {
                x : '50%',
                y : '50%'
            }

            console.log(obj)
            
            return {
                x: '50%',
                y: '50%'
            }
           
        }
    },
    created(){
        // console.log('created')
    },
    async mounted(){
        this.toi = createTimeOfInterest.fromDate(new Date());
        let moon = createMoon(this.toi)
        this.moon = await moon.getApparentGeocentricEquatorialSphericalCoordinates()
        

        console.log(this.moon.rightAscension)
    }    
}
</script>
<style >
    .Astro_Div{
        position:relative;
    }
    .top_SVG{
        width:500px;
        height:500px;
        position:absolute;
        left:0;
        top:0;
        z-index: -1;
    }
</style>