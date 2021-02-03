<template>
    <!-- component -->
    <div class="flex flex-col" >
        
        <div>
            <img class="w-full" :src="thumbnail">
        </div>
        
        <div class="px-10 my-4 py-6 bg-white rounded-lg shadow-md">
            <div class="flex justify-between items-center">
                <span class="font-light text-gray-600">{{ release_date }}</span>
                <button class="px-2 py-1 bg-gray-600 text-gray-100 font-bold rounded hover:bg-gray-500" href="#">{{ genre }}</button>
            </div>
            <div class="mt-2">
                <p class="text-2xl text-gray-700 font-bold hover:text-gray-600 cursor-pointer" >{{ title }}</p>
                <p v-if="short_description.length<80" class="mt-2 text-gray-600">{{ short_description }}</p>
                <p v-else class="mt-2 text-gray-600">{{ short_description.substring(0,80)+" ..." }}</p>
            </div>
            <div class="flex justify-between items-center mt-4">
                <a class="text-blue-600 hover:underline" :href="game_url" target="_blank" rel="noopener noreferrer">Read more</a>
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