<template >
    <div class="mygrid" ref="mygrid">
        <!-- <MygridUi /> -->
        <div class="mygrid_canvas">

            <div class="baseline" v-for="n in numBase" :style="{height : `${base}px`}"></div>
            
            <div class="col" v-for="(n,i) in col" :style="{
            width : `${colWidth}px`,
            left:`${colPos[i]}px`,
            borderLeft: `${colgap == 0 && i > 0 ? 0 : 1}px dotted rgba(255,0,0,0.5)`
            }"
            >
            <div class="colPad" v-if="colPad > 0" :style="{left:`${colPad/2}px`,right:`${colPad/2}px`}"></div>
            </div>

        </div>
        
    </div>
</template>
<script>
import MygridUi from './mygridUi.vue'
export default {
    data(){
        return {
            col: 5,
            colWidth: null,
            colgap:0,
            colgut:0,
            colPos : [],
            colPad :80,
            row : 4,
            base : 20,
            mygridheight : null,
            mygridwidth : null,
            numBase : null
        }
    },
    methods:{
        calcGrid(){
            this.mygridheight = this.$refs.mygrid.clientHeight
            this.mygridwidth = this.$refs.mygrid.clientWidth
            this.numBase = Math.trunc(this.mygridheight/this.base)
            this.colWidth = ( ( this.mygridwidth - (this.colgut*2) - (this.colgap*(this.col-1) ) ) / this.col )
            let newColPos = []
            for(let i = 0; i < this.col ; i++ ){
                let push
                if(i == 0){
                    push = this.colgut
                }else{
                    push = this.colgut + (i * this.colWidth) + (i * this.colgap)
                }  
                newColPos.push(push)
            }
            this.colPos = newColPos
        }
    },
    mounted(){
        this.calcGrid()
    },
    created() {
        window?.addEventListener("resize", this.calcGrid);
    },
    destroyed() {
        window.removeEventListener("resize", this.calcGrid);
    }
}
</script>
<style >
    .mygrid{
        position:absolute;
        z-index:10;
        top:0;
        left:0;
        right:0;
        bottom:0;
        pointer-events: none;
        user-select: none;
    }
    .mygrid_canvas{
        
        width:100%;
        height:100%;
    }
    .baseline{
        border-bottom:1px dotted rgba(0,0,255,0.5);
        width : 100%
    }
    .col{
        position:absolute;
        /* background:red; */
        /* height : 100%; */
        top:0;
        bottom:0;
        border-right:1px dotted rgba(255,0,0,0.5);
        
    }
    .colPad{
        position:absolute;
        top:0;
        bottom:0;
        border-right:1px dotted rgba(255,0,0,0.25);
        border-left:1px dotted rgba(255,0,0,0.25);
        /* background:red; */
    }
</style>