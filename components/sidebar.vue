<template >
    <div class="sidebar">
        <div class="side_head">
            
            <RouterLink to="/">
                
                <!-- <span>www.<br/></span> -->
                <h1 ><span :style="{marginLeft:'-5px'}">Yoav</span><br>Badt</h1>
                <!-- <h1>Badt</h1> -->
                
                
                <h2 >Portfolio</h2>
                <div class="label">www.yoavbadt.com</div>
            </RouterLink>
        </div>

        <div class="side_list">
            <h2>Projects</h2>
        <ContentList  path="/projects" v-slot="{ list }">

            <nav v-for="link in list" :key="link._path" class="link_box">
                <RouterLink :to="link._path">
                    {{ link.name}} 
                </RouterLink>
            </nav>

        </ContentList>
        </div>
    </div>
</template>
<script>
export default {
    
}
</script>
<style >
    .side_head{
        container-type: inline-size;
        /* padding-top:40px; */
        /* padding-left:40px; */
        border-bottom:1px dotted #8A837C;
        /* height: 220px; */
        color:#675c51;
    }
    .side_head:hover{
        background : #11a8ff;
        color: #F1F0ED;
    }
    .side_head h1,.side_head h2{
        color: inherit ;
    }
    .side_head a{
        transition: 0s;
        padding:40px;
        display: inline-block;
    }
    .side_head h1{
        /* font-family: 'Geist'; */
        /* font-size:1.75vw; */
        font-size: 16cqw;
        line-height:40px;
        font-weight: 600;
        letter-spacing: 1px;
        text-transform: none;
    }
    .side_head h1 span{
        font-weight:inherit;
    }
    .side_head h2{
        font-size: 10cqw;
        line-height:40px;
        font-weight: 300;
        /* color:#A8A29A; */
    }
    .side_head label{
        line-height:20px;
        margin:0;
    }
    .side_list{
        padding:40px 40px;
    }
    .side_list h2{
        margin-bottom:20px;
    }
    .link_box{
        /* border:1px solid red; */
        margin-bottom:10px;
    }
    
    nav a.router-link-active {
        color: #11a8ff;
    }
</style>