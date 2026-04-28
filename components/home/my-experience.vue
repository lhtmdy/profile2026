<template>
    <div class="overflow-hidden " v-fade:up>
        <SharedTabBox :info="tabList" @update-activeId="updateActiveId($event)" class="mb-7 lg:mb-16" />
        <div>
            <HomeExperienceDesktop :info="expList" v-if="screen === 'desktop' && activeId == 'experience'" />
            <HomeExperienceMobile :info="expList" v-else-if="screen === 'mobile' && activeId == 'experience'" />
            <HomeExperienceSkill v-else/>
        </div>
    </div>
</template>
<script setup>
const { width: winW } = useWindowSize();
const screen = computed(() =>
    winW.value > 1200 ? 'desktop' : 'mobile'
)
const tabList = ref(
    [
        {
            id: 'experience',
            title: '過往經歷'
        },
        {
            id: 'skill',
            title: '專業技能'
        }
    ]);
const activeId = ref(null);
const updateActiveId = (val => activeId.value = val)
const expList = ref([
    {
        id: 'iisi',
        logo: '/profile2026/image/iisi_logo.png',
        title: '資拓宏宇股份有限公司',
        subTitle: '前端工程師',
        date: '2023/12 - Now',
        desc: '在職期間參與了5個專案的開發維護，主要使用Vue做為開發框架，搭配Tailwind CSS與Naive ui建立一致的設計系統，並以Pinia進行狀態管理。具備良好的元件設計、模組化開發與維護能力。除了能獨立完成小專案開發外，我也主導大型專案的前端架構設計及開發流程規範。'
    },
    {
        id: 'digisalad',
        logo: '/profile2026/image/digisalad_logo1.png',
        title: '沙拉互動有限公司',
        subTitle: '前端工程師',
        date: '2023/02 - 2023/08',
        desc: '在職期間，主要以Nuxt.js(2和3)進行網站前端開發，與設計師、專案經理及後端工程師互相配合，順利開發及維護了5個專案。內容包含購物商場網站、飯店網站及各式官網。'
    },
    {
        id: 'tibame',
        logo: '/profile2026/image/tibame_logo.png',
        title: '緯育Tibame',
        subTitle: '前端工程師就業養成班',
        date: '2022/09 - 2023/01',
        desc: '在學期間，學習了網站前後端技術，順利完成了兩項專題'
    },

]);

</script>     