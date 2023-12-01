<template>
    <div id="app" class="min-h-screen flex items-center justify-center">
        <div class="bg-white p-8 rounded shadow-md w-full md:w-2/3 lg:w-1/2 xl:w-1/3">
            <h1 class="text-3xl font-bold mb-4">Nodots - tool voor genereren van link voor campagnes</h1>

            <label for="website" class="block text-sm font-medium text-gray-700 mb-2">Website URL:</label>
            <input v-model="website" placeholder="Website URL"
                class="w-full px-4 py-2 border border-gray-300 rounded mb-4 focus:outline-none focus:ring focus:border-blue-300">

            <label for="campaignId" class="block text-sm font-medium text-gray-700 mb-2">Campaign ID:</label>
            <input v-model="campaignId" placeholder="Campaign ID"
                class="w-full px-4 py-2 border border-gray-300 rounded mb-4 focus:outline-none focus:ring focus:border-blue-300">

            <label for="campaignSource" class="block text-sm font-medium text-gray-700 mb-2">Campaign Source:</label>
            <input v-model="campaignSource" placeholder="Campaign Source"
                class="w-full px-4 py-2 border border-gray-300 rounded mb-4 focus:outline-none focus:ring focus:border-blue-300">

            <label for="campaignMedium" class="block text-sm font-medium text-gray-700 mb-2">Campaign Medium:</label>
            <input v-model="campaignMedium" placeholder="Campaign Medium"
                class="w-full px-4 py-2 border border-gray-300 rounded mb-4 focus:outline-none focus:ring focus:border-blue-300">

            <label for="campaignName" class="block text-sm font-medium text-gray-700 mb-2">Campaign Name:</label>
            <input v-model="campaignName" placeholder="Campaign Name"
                class="w-full px-4 py-2 border border-gray-300 rounded mb-4 focus:outline-none focus:ring focus:border-blue-300">

            <label for="utmId" class="block text-sm font-medium text-gray-700 mb-2">UTM ID:</label>
            <input v-model="utmId" placeholder="UTM ID"
                class="w-full px-4 py-2 border border-gray-300 rounded mb-4 focus:outline-none focus:ring focus:border-blue-300">

            <button @click="generateLink"
                class="w-full bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-600 focus:outline-none focus:ring focus:border-blue-300">Generate
                Link</button>

            <div id="generatedLink" class="mt-6 text-sm text-gray-700 break-words">{{ generatedLink }}</div>
        </div>
    </div>
</template>
  
  

<script>
export default {
    name: 'LinkingTool',
    components: {},
    props: {},
    data() {
        return {
            website: '',
            campaignId: '',
            campaignSource: '',
            campaignMedium: '',
            campaignName: '',
            utmId: '',
            generatedLink: ''
        };
    },
    computed: {},
    watch: {},
    created() { },
    mounted() {
        this.generateLink();
    },

    methods: {
        generateLink() {
            this.generatedLink = `${this.website}?utm_source=${this.campaignSource}&utm_medium=${this.campaignMedium}&utm_campaign=${this.campaignName}&utm_id=${this.utmId}`;
        }
    },

}
</script>

