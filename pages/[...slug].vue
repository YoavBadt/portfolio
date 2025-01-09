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
                 main_2
            </div>
        </ContentDoc>
        
   </main>
</template>
<script>
export default {
    
}
</script>
<style >
    .label{
        color:rgba(0,0,0,0.5);
        text-transform: capitalize;
        font-size:12px;
        line-height:20px;
        /* margin-bottom:5px; */
        font-weight: 300;
    }
    .main_1_h1{
        line-height:40px;
        margin-bottom: 40px;
        font-size: 10cqw;
    }
    .main_1_desc{
        font-weight: 500;
        line-height: 20px;
        margin-bottom:40px;
    }
    .main_1_p p{
        font-size:14px;
        line-height:20px;
        font-weight: 400;
        margin-bottom:20px;
        /* font-size: 5cqw; */
        /* font-size:1px; */
    }
</style>