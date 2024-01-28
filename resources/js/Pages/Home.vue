<script setup>
    import { ref, onMounted, toRefs } from 'vue';
    import { Head, Link, router } from '@inertiajs/vue3';
    import MainLayout from '@/Layouts/MainLayout.vue';

    import LikesSection from '@/Components/LikesSection.vue';

    import 'vue3-carousel/dist/carousel.css'
    import { Carousel, Slide, Navigation } from 'vue3-carousel'

    import DotsHorizontal from 'vue-material-design-icons/DotsHorizontal.vue';

    let wWidth = ref(window.innerWidth)
    let currentSlide = ref(0)
    let currentPost = ref(null)
    let openOverlay = ref(false)

    const props = defineProps({ posts: Object, allUsers: Object })
    const { posts, allUsers } = toRefs(props)

    onMounted(() => {
    window.addEventListener('resize', () => {
        wWidth.value = window.innerWidth
    })
})

const images = ref([
    { src: 'https://picsum.photos/id/20/300/320', name: 'Name Here', link: '/image-1' },
    { src: 'https://picsum.photos/id/21/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/22/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/23/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/24/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/25/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/26/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/27/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/28/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/29/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/30/300/320', name: 'Name Here', link: '/image-2' },
    { src: 'https://picsum.photos/id/31/300/320', name: 'Name Here', link: '/image-2' }
]);


</script>

<template>
    <Head title="Instagram" />
    <MainLayout>
        <div class="grid grid-cols-1">
        <div class="lg:pl-0 md:pl-[100px]">
            <Carousel
                v-model="currentSlide"
                class="max-w-[700px] mx-auto"
                :items-to-show="wWidth >= 768 ? 8 : 6"
                :items-to-scroll="4"
                :wrap-around="true"
                :transition="500"
                snapAlign="start"
            >
                <Slide v-for="(image, index) in images" :key="index">
                    <Link :href="image.link" class="relative mx-auto text-center mt-4 px-2 cursor-pointer">
                        <div class="absolute z-[-1] -top-[5px] left-[4px] rounded-full rotate-45 w-[64px] h-[64px] contrast-[1.3]  bg-gradient-to-t from-yellow-300 to-purple-500 via-red-500">
                        <div class="rounded-full ml-[3px] mt-[3px] w-[58px] h-[58px] bg-white" />
                        </div>
                        <img class="rounded-full w-[56px] h-[56px] -mt-[1px]" :src="image.src" :alt="image.name">
                        <div class="text-xs mt-2 w-[60px] truncate text-ellipsis overflow-hidden">{{ image.name }}</div>
                    </Link>
                </Slide>
                <template #addons>
                    <Navigation />
                </template>
            </Carousel>

            <div id="Posts" class="px-2 max-w-[600px] mx-auto mt-4">
                <div class="flex items-center justify-between py-2">
                    <div class="flex items-center">
                        <Link href="" class="flex items-center">
                            <img class="rounded-full w-[38px] h-[38px]" src="https://picsum.photos/id/81/300/320">
                            <div class="ml-4 font-extrabold text-[15px]">Name Here</div>
                        </Link>
                        <div class="flex items-center text-[15px] text-gray-500">
                            <span class="-mt-5 ml-2 mr-[5px] text-[35px]">.</span>
                            <div>01/05/2023</div>
                        </div>
                    </div>

                    <DotsHorizontal class="cursor-pointer" :size="27"/>
                </div>
                <div class="bg-black rounded-lg w-full min-h-[400px] flex items-center">
                    <img class="mx-auto w-full" src="https://picsum.photos/id/69/300/320" />
                </div>

                <LikesSection />

                <div class="text-black font-extrabold py-1">3 likes</div>
                <div>
                    <span class="text-black font-extrabold">Name Here</span>
                    Lorem ipsum dolor sit amet consectetur adipisicing elit.
                </div>
                <button
                    class="text-gray-500 font-extrabold py-1"
                >
                    View all 4 comments
                </button>
            </div>
            <div class="pb-1"></div>
            <div id="Posts" class="px-2 max-w-[600px] mx-auto mt-2">
                <div class="flex items-center justify-between py-2">
                    <div class="flex items-center">
                        <Link href="" class="flex items-center">
                            <img class="rounded-full w-[38px] h-[38px]" src="https://picsum.photos/id/90/300/320">
                            <div class="ml-4 font-extrabold text-[15px]">Name Here</div>
                        </Link>
                        <div class="flex items-center text-[15px] text-gray-500">
                            <span class="-mt-5 ml-2 mr-[5px] text-[35px]">.</span>
                            <div>01/06/2023</div>
                        </div>
                    </div>

                    <DotsHorizontal class="cursor-pointer" :size="27"/>
                </div>
                <div class="bg-black rounded-lg w-full min-h-[400px] flex items-center">
                    <img class="mx-auto w-full" src="https://picsum.photos/id/46/300/320" />
                </div>

                <LikesSection />

                <div class="text-black font-extrabold py-1">3 likes</div>
                <div>
                    <span class="text-black font-extrabold">Name Here</span>
                    Lorem ipsum dolor sit amet consectetur adipisicing elit.
                </div>
                <button
                    class="text-gray-500 font-extrabold py-1"
                >
                    View all 4 comments
                </button>
            </div>
            <div class="pb-1"></div>
            <div id="Posts" class="px-2 max-w-[600px] mx-auto mt-2">
                <div class="flex items-center justify-between py-2">
                    <div class="flex items-center">
                        <Link href="" class="flex items-center">
                            <img class="rounded-full w-[38px] h-[38px]" src="https://picsum.photos/id/82/300/320">
                            <div class="ml-4 font-extrabold text-[15px]">Name Here</div>
                        </Link>
                        <div class="flex items-center text-[15px] text-gray-500">
                            <span class="-mt-5 ml-2 mr-[5px] text-[35px]">.</span>
                            <div>01/07/2023</div>
                        </div>
                    </div>

                    <DotsHorizontal class="cursor-pointer" :size="27"/>
                </div>
                <div class="bg-black rounded-lg w-full min-h-[400px] flex items-center">
                    <img class="mx-auto w-full" src="https://picsum.photos/id/85/300/320" />
                </div>

                <LikesSection />

                <div class="text-black font-extrabold py-1">3 likes</div>
                <div>
                    <span class="text-black font-extrabold">Name Here</span>
                    Lorem, ipsum dolor sit amet consectetur adipisicing elit.
                </div>
                <button
                    class="text-gray-500 font-extrabold py-1"
                >
                    View all 4 comments
                </button>
            </div>
            <div class="pb-1"></div>
            <div id="Posts" class="px-2 max-w-[600px] mx-auto mt-2">
                <div class="flex items-center justify-between py-2">
                    <div class="flex items-center">
                        <Link href="" class="flex items-center">
                            <img class="rounded-full w-[38px] h-[38px]" src="https://picsum.photos/id/16/300/320">
                            <div class="ml-4 font-extrabold text-[15px]">Name Here</div>
                        </Link>
                        <div class="flex items-center text-[15px] text-gray-500">
                            <span class="-mt-5 ml-2 mr-[5px] text-[35px]">.</span>
                            <div>01/09/2023</div>
                        </div>
                    </div>

                    <DotsHorizontal class="cursor-pointer" :size="27"/>
                </div>
                <div class="bg-black rounded-lg w-full min-h-[400px] flex items-center">
                    <img class="mx-auto w-full" src="https://picsum.photos/id/91/300/320" />
                </div>

                <LikesSection />

                <div class="text-black font-extrabold py-1">3 likes</div>
                <div>
                    <span class="text-black font-extrabold">Name Here</span>
                    Lorem ipsum dolor sit amet consectetur adipisicing elit.
                </div>
                <button
                    class="text-gray-500 font-extrabold py-1"
                >
                    View all 4 comments
                </button>
            </div>
            <div class="pb-1"></div>
        </div>
    </div>

    </MainLayout>
</template>


<style>
    .carousel__prev,
    .carousel__next,
    .carousel__prev:hover,
    .carousel__next:hover {
        color: rgb(49, 49, 49);
        background-color: rgb(255, 255, 255);
        border-radius: 100%;
        margin: 0 20px;
    }
</style>