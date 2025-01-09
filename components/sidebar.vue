<template >
    <div class="sidebar">
        <div class="side_head">
            
            <RouterLink to="/">
                <h1>
                <!-- <span>www.<br/></span> -->
                Yoav<br/>
                Badt<br/>
                <span>Portfolio</span>
                </h1>
                <div class="label">www.yoavbadt.com</div>
            </RouterLink>
        </div>

        <div class="side_list">
            <h2>Projects</h2>
        <ContentList  path="/projects" v-slot="{ list }">

            <div v-for="link in list" :key="link._path" class="link_box">
                <RouterLink :to="link._path">
                    <h3>{{ link.name}}</h3>
                </RouterLink>
            </div>

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
        padding-top:40px;
        padding-left:20px;
        border-bottom:1px dotted #8A837C;
        height: 220px;
        container-type: inline-size;
    }
    .side_head h1{
        /* font-family: 'Geist'; */
        /* font-size:1.75vw; */
        line-height:40px;
        font-weight: 600;
        letter-spacing: 1px;
        font-size: 18cqw;
        text-transform: none;
        color:#8A837C
    }
    .side_head h1 span{
        font-size: 13cqw;
        font-weight: 300;
        color:#A8A29A;
    }
    .side_list{
        padding:20px;
    }
    .link_box{
        /* border:1px solid red; */
        margin-bottom:10px;
    }
</style>