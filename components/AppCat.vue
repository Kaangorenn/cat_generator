<template>
    <div class="p-5">
        <div v-if="catImage" class="h-full w-full">
            <div class="p-5 bg-white/10 rounded-xl backdrop-blur-md border-[1px] border-white/50">
                <NuxtImg class="mx-auto w-full max-h-[500px] rounded-lg" :src="catImage" alt="Random Cat"></NuxtImg>
            </div>
        </div>
        <div :class="{ 'fixed bottom-8 px-8 w-full h-20 left-0': catImage }" class="">
            <div :class="{ 'w-full mx-auto': catImage }" class="bg-white/10 rounded-xl backdrop-blur-md p-5 block border-[1px] border-white/50 mx-auto">
                <div class="w-full">
                    <button @click="getCat" class="text-white text-center bg-black w-full py-2 px-5 rounded-md text-md md:text-2xl">Get Random Cat Image</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            catImage: null,
        };
    },
    methods: {
        async getCat() {
            const response = await fetch(`https://api.thecatapi.com/v1/images/search`);
            const data = await response.json();
            this.catImage = data;
            console.log(this.catImage);
        },
    },
};
</script>