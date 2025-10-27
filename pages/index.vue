<template >
   <main class="indexMainBox">
      <!-- <Mygrid /> -->
      <div class="indexGalleryItem" :style="{gridColumn: '1/span 2',gridRow: '1/span 2',}">
         <NuxtImg class="indexImg" :style="{height:'100%'}" src="barong.jpg" preload />
      </div>
      <div class="indexGalleryItem" :style="{gridColumn: '2/span 2',gridRow: '3/span 2',}">
         <NuxtImg class="indexImg" :style="{width:'100%'}" src="blue2.jpg" preload />
      </div>
      
      <div class="indexGalleryItem" :style="{gridColumn: '4/span 1',gridRow: '3/span 2',}">
         <NuxtImg class="indexImg"  :style="{width:'100%'}" src="senhadrin.png" preload />
      </div>
      <div class="indexGalleryItem" :style="{gridColumn: '1/span 1',gridRow: '3/span 1',}">
         <NuxtImg class="indexImg" :style="{height:'100%'}" src="fsight1.png" preload />
      </div>
      
      <div class="indexGalleryItem" :style="{gridColumn: '1/span 1',gridRow: '4/span 1',}">
         <NuxtImg class="indexImg" :style="{height:'100%'}" src="synth1.png" preload />
      </div>
        <!-- <div class="indexGalleryItem" :style="{gridColumn: '4/span 1',gridRow: '3/span 2',}">
         <NuxtImg class="indexImg"    :style="{height:'100%'}" src="radical1.png" preload />
      </div>  -->

      
      <div class="indexMain">
         <ContentDoc v-slot="{ doc }">
            <div class="indexMain_wrap">

               <h1 class="indexMain_h1">Hello, My name is Yoav Badt.</h1>
               <h2 class="indexMain_h2">I am a graphic artist & web designer. I code with Javascript and build with <a target="_blank" href="https://vuejs.org">VueJs</a>. I am also a painter & illustrator. I made this Jamstack portfolio website with <a target="_blank" href="https://nuxt.com">Nuxt.js</a>,  <a target="_blank" href="https://content.nuxt.com">@Nuxt/Content</a>, and deployed it from Github to <a target="_blank" href="https://www.netlify.com/">Netlify</a>.</h2>
            </div>
            <!-- <h1 class="indexMain_h1">{{ doc.title}}</h1> -->
            <!-- <h2 class="indexMain_h2">{{ doc.subtitle}}</h2> -->
            <!-- <ContentRendererMarkdown :value="doc" /> -->
         </ContentDoc>
      </div>
      <!-- <ContentRenderer :value="doc"  class="mainBox" tag="div"/> -->
      <!-- <ContentRenderer :value="doc">
         <slot />
         
      </ContentRenderer> -->
   </main>
</template>
<script>
import Mygrid from './components/mygrid/mygrid.vue'
export default {
    
}
</script>
<style>
      .indexGalleryItem{
         outline: 1px dotted lightgrey;
         /* box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1); */
         /* border-radius:3px; */
         overflow:hidden;
         
         display: flex;
         align-items: center;
         justify-content: center;
         /* background:red; */
      }
     .indexImg{
        /* filter: grayscale(100%) */
        /* object-fit : cover; */
     }
     .indexImg:hover{
        /* filter: grayscale(0%) */
     }
     

     .indexMainBox{
         grid-template-columns: repeat(6,1fr);
         grid-template-rows: repeat(4,1fr);
         /* gap:20px; */
         /* padding: 20px   */
     }
    .indexMain{
      outline: 1px dotted lightgrey;
      /* border-radius:3px;  */
      padding:40px;

      /* font-size:24px;
      line-height:  */
      /* position:relative; */
      /* align-self: center; */
      grid-column: 3/span 2;
      grid-row: 1/span 2;
      display: flex;
      align-items: center; 
      justify-content: center; 
    }
    .indexMain_wrap{
    }
    .indexMain_h1{
      font-size:20px;
      line-height:40px;
      font-weight:600;
    }
    .indexMain_h2{
      font-size:20px;
      line-height:30px;
      font-weight:300;
      text-transform: none; 
    }

    .indexMain_h2 a{
      /* color:#11a8ff; */
      border-bottom:2px solid #11a8ff;
      font-weight: 400;
      margin-bottom:0px;
    }
</style>