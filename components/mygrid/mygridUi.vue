<template >
    <div class="mygridUi" :style="{top:`${top}px`,left: `${left}px`}">
        <div class="mygrid_head"  @mousedown="drag=!drag" @mousemove="startDrag" @mouseup="drag=!drag"></div>
        <div class="mygrid_box">
            content
        </div>
    </div>
</template>
<script>
export default {
    data(){
        return{
            top: 20,
            left : 20,
            drag : false,
            movex: null,
            movey: null,
        }
    },
    watch: {
        drag(newDrag,oldDrag){
            // newDrag ? this.top += 1 : null
        }
    },
    methods:{
        startDrag(e){
            if(this.drag){
                this.top += e.movementY;
                this.left += e.movementX 
            }
        },
        
    },
    created() {
        window?.addEventListener("mouseup", ()=>{this.drag = false});
        window?.addEventListener("mousemove", this.startDrag);
    },
    destroyed() {
        window.removeEventListener("mouseup", ()=>{this.drag = false});
        window.removeEventListener("mousemove", this.startDrag);
    }
}
</script>
<style >
    .mygridUi{
        position:absolute;
        top:20px;
        left:20px;
        width:200px;
        height:600px;
        
        border-radius:3px;
        background:white;
        outline:1px solid grey;
        pointer-events: auto;
        z-index:3;
    }
    .mygrid_head{
        width:100%;
        height:20px;
        background:grey;
    }
    .mygrid_box{
        height:100%;
        width:100%;
        padding:10px;
    }
</style>