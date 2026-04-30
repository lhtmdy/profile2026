<template>
    <div class="container pb-[60px] md:pb-[120px]">
        <div class="grid grid-cols-4 gap-4 md:grid-cols-6 md:gap-10 w-[100%] md:w-[80%] mx-auto hidden-content">
            <div class="flex items-center justify-center" v-for="(i,idx) in skillsArr" :key="`${i}-${idx}`" v-fade:in >
                <img :src="`/profile2026/image/skills/${i}.png`" :alt="i" :title="i" >
            </div>
        </div>
    </div>
</template>
<script setup>
    const skillsArr = ref(['html','css','javascript','vue','nuxt','react','pinia','cicd','tailwindcss','sass','bootstrap','naive_ui','php','mysql','jquery','git','github','bitbucket','gitlab','postman',
    'swagger','python','java','figma']);
</script>