<script setup>

import legalItems from '../data/legal.js';
import { ref } from 'vue';

let isOpen = ref(1);


</script>

<template>
    <div id="legal" class="container mx-auto px-5">
    <section class="py-16">
        <div class="mt-10">
            <ul class="flex flex-col items-center md:flex-row justify-center font-theme-heading">
                <li v-for="item in legalItems" :key="item.id" 
                    :class="isOpen === item.id ? 'md:border-b-4 md:border-theme-secondary' : ''" 
                    class="w-full md:w-56 cursor-pointer hover:text-theme-secondary transition duration-200 border-b-2 border-t-2 md:border-t-0 flex justify-center">
                    <a @click.prevent="isOpen = item.id" 
                       :href="item.url" 
                       target="_blank" 
                       rel="noopener noreferrer"
                       :class="isOpen === item.id ? 'border-theme-secondary' : ''" 
                       class="py-5 md:border-b-0 border-b-4">
                        {{ item.name }}
                    </a>
                </li>
            </ul>
        </div>

        <div class="mt-16">
            <!-- Tab Content -->
            <template v-for="item in legalItems" :key="item.id">
                <div v-show="isOpen === item.id" class="grid gap-32 lg:grid-cols-2 items-center">
            <!--         <div class="relative">
                        <img class="z-10 w-full" :src="item.imageUrl" alt="Legal document illustration" />
                        <div class="-z-10 bg-theme-primary h-52 w-96 sm:h-80 sm:w-full rounded-r-full absolute -left-56 -bottom-16"></div>
                    </div> -->
                    <div>
                        <h3 class="font-theme-heading text-2xl md:text-3xl font-medium text-center lg:text-left">{{ item.title }}</h3>
                        <p class="mt-7 font-theme-content text-lg text-theme-grayish-blue text-center lg:text-left">{{ item.description }}</p>
                        <a :href="item.url" target="_blank" rel="noopener noreferrer" 
                           class="mt-5 inline-block bg-theme-secondary text-white px-6 py-2 rounded hover:bg-theme-primary transition duration-200">
                            Read More
                        </a>
                    </div>
                </div>
            </template>
            <!-- Tab Content -->
        </div>
    </section>
</div>
</template>
