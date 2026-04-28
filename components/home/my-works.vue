<template>
    <div class="overflow-hidden py-[60px] md:py-[120px] bg-primary-02" id="works">
        <div class="container">
            <h2 class="mb-5 text-primary-01">作品集</h2>
        </div>
        <!-- swiper -->
        <div class="container-left" v-fade:up>
            <Swiper :slides-per-view="1.2" :space-between="24" :breakpoints="{
                '768': {
                    slidesPerView: 1.8,
                    spaceBetween: 30,
                },
                '1200': {
                    slidesPerView: 2.5,
                    spaceBetween: 30,
                },
            }" :speed="600" :initial-slide="0" :slide-to-clicked-slide="false" @swiper="initSwiper" class="w-[100%]">
                <SwiperSlide v-for="item in works_info" :key="item.id" class="swiper-slide">
                    <HomeWorksIosCard :info="item" v-if="isSafari" />
                    <HomeWorksCard :info="item" v-else />
                </SwiperSlide>
            </Swiper>
            <div class="flex items-center justify-between w-fit mt-[30px]">
                <button class="btn-i-primary--sm md:btn-i-primary--md mr-3 group" :class="{ 'invisible': isBeginning }"
                    @click="slidePrev">
                    <NuxtIcon name="arr-right" class="text-[white] group-hover:text-primary-03 z-[2] relative rotate-180" />
                </button>
                <button class="btn-i-primary--sm md:btn-i-primary--md group" :class="{ 'invisible': isEnd }"
                    @click="slideNext">
                    <NuxtIcon name="arr-right" class="text-[white] group-hover:text-primary-03 z-[2] relative" />
                </button>
            </div>
        </div>
    </div>
</template>
<script setup>
const works_info = ref([
    {
        id: 'ACS',
        title: '資通安全入口網',
        image: '/profile2026/image/works/acs.png',
        description: '本系統為多角色、多模組之大型業務平台，服務對象涵蓋署方、外部機關及一般民眾。系統包含帳號管理、績效評核、會議／活動報名、資安履歷等 13 個核心模組，具備高複雜度業務邏輯與跨單位協作需求，需在多角色權限與大量資料互動情境下維持系統穩定性與一致性。',
        skill: ['Vue.js', 'Tailwind.css','Naive ui']
    },
    {
        id: 'rdss',
        title: '研發替代役',
        image: '/profile2026/image/works/rdss.png',
        description: '本網站為研發替代役專屬的線上系統，提供替代役男申請、審核、管理等功能。系統包含多種使用者角色，如役男、機關、管理員等，並具備複雜的權限控制與流程管理需求。系統需確保資料安全性與穩定性，同時提供良好的使用者體驗，以提升替代役男的申請效率與滿意度。',
        skill: ['Vue.js', 'Tailwind.css','Naive ui']
    },
    {
        id: 'ti',
        title: '技能檢定中心',
        image: '/profile2026/image/works/ti.png',
        description: '本系統為技能檢定中心資訊安全管理平台，提供完整的資安治理解決方案，包括：資產安全管理、安全維護機制、稽核合規作業等。',
        skill: ['Vue.js', 'Tailwind.css','Naive ui','Bootstrap']
    },
    {
        id: 'xita',
        title: 'XITA',
        image: '/profile2026/image/works/xita.png',
        url: 'https://xita.co/#/',
        description: 'XITA是以用戶體驗為先的開網店平台，5分鍾開店、1站式管理預約、4個步驟即刻完成客人預約，最重要是費用由$0起！',
        skill: ['Vue.js',  'Tailwind.css']
    },
    {
        id: 'airside',
        title: 'Airside',
        image: '/profile2026/image/works/airside_logo.png',
        url: 'https://www.airside.com.hk/',
        description: 'AIRSIDE是位於啟德發展區的190萬平方呎多用途商業空間。用心感受每次呼吸，擁抱「和而為一」的生活概念，與自己、身邊的人和自然環境重新聯繫，體會節奏的變化。',
        skill: ['Vue.js', 'Nuxt2', 'Tailwind.css']
    },
    {
        id: 'nft',
        title: 'NF Touch',
        image: '/profile2026/image/works/nft_logo.png',
        url: 'https://www.nftouch.com.hk/en',
        description: '本網站的客戶為南豐集團。南豐集團的「NF Touch南豐會員計劃」，讓會員在旗下商場消費儲分。',
        skill: ['Vue.js', 'Nuxt3', 'Tailwind.css']
    },
    {
        id: 'wynn',
        title: 'Wynn',
        image: '/profile2026/image/works/wynn_logo.png',
        url: 'https://www.wynnresortsmacau.com/en/wynn-macau/whats-on/art-macao2023',
        description: '本網站客戶為永利度假村以及旗下兩家頂級酒店和度假村：永利澳門和永利皇宮。以飯店介紹及訂房服務為主。',
        skill: ['Vue.js', 'Nuxt2', 'Tailwind.css']
    },
    {
        id: '5fcoffee',
        title: '5F COFFEE',
        image: '/profile2026/image/works/5f_coffee.png',
        url: 'https://c26931230.github.io/5F_Coffee_v3/',
        description: '本網站為個人專題網站。5fcoffee創立於2020年，起初是啡啡館，除了喜歡分享咖啡外，也致力將咖啡知識推廣給大家，在2021年創立了咖啡教室，讓想在咖啡領域發展的人，有專業的學習環境。',
        skill: ['HTML', 'CSS', 'JavaScript', 'Vue.js', 'jQuery']
    },
    {
        id: 're_outfit',
        title: 'RE OUTFIT',
        image: '/profile2026/image/works/re_outfit.png',
        url: 'https://tibamef2e.com/cgd103/g2/',
        description: '本網站為團體專題作品。在近年快時尚的風潮中，成衣製造一直有生產過剩的問題，一旦衣服過季時就會造成存貨過多，帶來服飾滯銷問題，造成生產資源的浪費。 為了解決剩餘服飾問題，我們提供造型師搭配服務，將過剩衣服重新搭配，並幫助消費者找到自己的風格，達到資源有效利用。',
        skill: ['HTML', 'CSS', 'JavaScript', 'SCSS', 'Vue.js', 'PHP', 'My SQL']
    },
]);
// swiper
const mySwiper = ref(null);
const initSwiper = (swiper) => {
    mySwiper.value = swiper;
};
const slidePrev = () => {
    mySwiper.value.slidePrev();
};
const slideNext = () => {
    mySwiper.value.slideNext();
};
const isBeginning = computed(() =>
    mySwiper?.value?.isBeginning ?? null
);
const isEnd = computed(() =>
    mySwiper?.value?.isEnd ?? null
);
const isSafari = ref(false);
onMounted(() => {
    const userAgent = navigator.userAgent;
    if (userAgent.indexOf('Safari') !== -1 && userAgent.indexOf('Chrome') === -1) {
        isSafari.value = true;
    }
});
</script>