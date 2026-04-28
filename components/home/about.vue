<template>
    <div class="text-center container mb-[30px] md:mb-20" id="about" v-fade:up>
        <h2 class="mb-6">{{ aboutInfo.title }}</h2>
        <p class="text-grey-700">{{ aboutInfo.description }}</p>
    </div>
</template>
<script setup>
const aboutInfo = ref(
    {
        title:'關於我',
        description:'您好，我是李欣恬，目前在「資拓宏宇」工作擔任前端工程師一職，累積了 3 年以上的實務經驗。我參與過多個專案，從能獨立完成小型開發，到負責大型專案的前端架構與流程規劃。過去也曾在專案初期與 10 多位後端工程師合作串接 API，並帶領前端團隊一起完成開發。在團隊中，我習慣扮演溝通與整合的角色，讓不同背景的成員可以順利合作，也幫助專案穩定推進。過去也有帶 junior 的經驗，會一起檢視程式碼、分享開發觀念，讓整體品質更一致。'
    }
)
</script>
