<template>
    <!-- component -->
    <div class="mb-6 tracking-wide" >
            <div class="md:flex-shrink-0">
                <img :src="thumbnail">
            </div>
    <div class="max-w-4xl px-10 my-4 py-6 bg-white rounded-lg shadow-md">
        <div class="flex justify-between items-center">
            <span class="font-light text-gray-600">{{ release_date }}</span>
            <button class="px-2 py-1 bg-gray-600 text-gray-100 font-bold rounded hover:bg-gray-500" href="#">{{ genre }}</button>
        </div>
        <div class="mt-2">
            <p class="text-2xl text-gray-700 font-bold hover:text-gray-600 cursor-pointer" >{{ title }}</p>
            <p class="mt-2 text-gray-600">{{ short_description }}</p>
        </div>
        <div class="flex justify-between items-center mt-4">
            <a class="text-blue-600 hover:underline" :href="{game_url}">Read more</a>
        </div>
    </div>
    </div>
</template>

<script>
// @ is an alias to /src

export default {
    name: 'MyCard',
    props: {
        title: String,
        thumbnail: String,
        short_description: String,
        genre: String,
        // platform: String,
        // publisher: String,
        release_date: String,
        game_url: String
    }   
}
</script>