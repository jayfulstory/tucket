<script setup lang="ts">
import gsap from 'gsap';

    
    const handleCard = (e:MouseEvent, ratio: number) => {
        const x = gsap.utils.mapRange(0, 700, -1, 1);
        const y = gsap.utils.mapRange(0, 250, -1, 1);
        const target = e.target as HTMLElement; 
        target.style.transform = `
            perspective(400px)
            rotateX(${y(e.offsetY) * ratio}deg)
            rotateY(${x(e.offsetX) * ratio * -1}deg)
        `
    }
    const handleLeave = (e:MouseEvent) => {
        const target = e.target as HTMLDivElement
        target.style.transform = `
            rotateX(0deg)
            rotateY(0deg)
        `
    };

</script>
<template>
    <div ref="ani" @mousemove="(e) => handleCard(e, 5)" @mouseleave="e => handleLeave(e)"
        class="grid grid-cols-[500px_200px] w-[700px] h-[250px] drop-shadow-xl">

        <div class="grid grid-rows-[48px_1fr] rounded-xl overflow-hidden pointer-events-none">
            <div class="flex items-center px-4 bg-gradient-to-r from-blue-500 to-blue-400 from-40%">
                <img src="../../assets/logo.png" class="w-[32px] h-[32px]" alt="gxpのロゴ">
                <h1 class="text-white font-bold ml-2">GXP AIRLINE</h1>
            </div>

            <div class="flex gap-4 p-4 bg-white overflow-hidden">
                <img src="../../assets/poke.png" class="w-32 h-full object-cover" alt="プロフィール写真">
                <div class="relative flex flex-col justify-around w-full h-full bg-[url('/src/assets/map.png')] bg-no-repeat bg-[-500px_-150px] bg-[length:250%] fade-out-border">
                    <svg class="absolute top-0 left-0" width="100%" height="100%">
                        <path d="M119,145 A 80,80 0 0 1 192,38" stroke="red" stroke-width="2" fill="none" stroke-dasharray="5,5" stroke-linecap="round"/>
                    </svg>
                    <div class="flex justify-around">
                        <div class="text-center">
                            <h3 class=" text-4xl font-bold">CGK</h3>
                            <p><small class="">jakarta</small></p>
                            <p class="font-bold">2024/00/00</p>
                        </div>
                        <div class="text-center">
                            <h3 class=" text-4xl font-bold">CGK</h3>
                            <p><small class="">jakarta</small></p>
                            <p class="font-bold">2024/00/00</p>
                        </div>
                    </div>
                    <div class="border border-orange-400 h-16">
                        contents
                    </div>
                </div>
            </div>
        </div>

        <div class="relative grid grid-rows-[48px_1fr] bg-white overflow-hidden rounded-xl pointer-events-none">
            <div class="relative flex items-center px-4 bg-blue-400">
                <div class="absolute left-0 top-0 h-[48px] w-0  border-l border-dotted border-white"></div>
                <div class="border border-orange-400 w-full">contents</div>
            </div>
            <div class="relative flex flex-col justify-between items-center gap-2 px-4 py-2">
                <div class="absolute left-0 top-0 h-full w-0  border-l border-dotted border-gray-400">
                </div>
                <div class="border border-orange-400 w-full h-full">
                    contents
                </div>
                <img src="../../assets/barcode.png" class="" alt="バーコード">
            </div>
            <div class="absolute top-1/2 left-1/2 w-[150%] translate-x-[-50%] translate-y-[-50%]">
                <img src="../../assets/gxplogo.png" class="w-full h-full" alt="">
            </div>
        </div>

    </div>
</template>