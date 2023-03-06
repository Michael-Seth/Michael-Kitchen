<template>
    <footer class="bg-green-800 text-white dark:bg-gray-900 mt-20">
        <div class="container flex flex-col items-center justify-between px-6 py-8 mx-auto lg:flex-row">
            <a href="#">
                <img class="w-auto h-7" src="https://merakiui.com/images/full-logo.svg" alt="">
            </a>

            <div class="flex flex-wrap items-center justify-around gap-4 mt-6 lg:gap-12 lg:mt-0">
                <router-view :to="{ name: 'home' }"
                    class="text-sm text-gray-600 transition-colors duration-300 dark:text-gray-200 hover:text-blue-500 dark:hover:text-blue-400">
                    Home
                </router-view>

                <router-view :to="{ name: 'ingredients' }"
                    class="text-sm text-gray-600 transition-colors duration-300 dark:text-gray-200 hover:text-blue-500 dark:hover:text-blue-400">
                    Ingredients
                </router-view>
            </div>

            <p class="mt-6 text-sm text-gray-100 lg:mt-0 dark:text-gray-400">© Copyright 2023 Michael's Kitchen. </p>
        </div>
    </footer>
</template>