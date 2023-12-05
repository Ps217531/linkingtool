<template>
    <div id="app" class="min-h-screen flex items-center justify-center">
        <div class="bg-white p-4 md:p-8 rounded-md shadow-md w-full md:w-2/3 lg:w-1/2 xl:w-1/3">
            <h1 class="text-2xl md:text-3xl font-bold mb-4">Nodots - tool voor genereren van link voor campagnes</h1>

            <div class="mb-4">
                <label for="website" class="block text-sm font-medium text-gray-700 mb-2">Website URL:</label>
                <input v-model="website" @input="generateLink" placeholder="Website URL"
                    class="w-full px-4 py-2 border border-gray-300 rounded focus:outline-none focus:ring focus:border-blue-300">
            </div>

            <div class="mb-4">
                <label for="campaignId" class="block text-sm font-medium text-gray-700 mb-2">Campaign ID:</label>
                <input v-model="campaignId" @input="generateLink" placeholder="Campaign ID"
                    class="w-full px-4 py-2 border border-gray-300 rounded focus:outline-none focus:ring focus:border-blue-300">
            </div>

            <div class="mb-4">
                <label for="campaignSource" class="block text-sm font-medium text-gray-700 mb-2">Campaign Source:</label>
                <input v-model="campaignSource" @input="generateLink" placeholder="Campaign Source"
                    class="w-full px-4 py-2 border border-gray-300 rounded focus:outline-none focus:ring focus:border-blue-300">
            </div>

            <div class="mb-4">
                <label for="campaignMedium" class="block text-sm font-medium text-gray-700 mb-2">Campaign Medium:</label>
                <input v-model="campaignMedium" @input="generateLink" placeholder="Campaign Medium"
                    class="w-full px-4 py-2 border border-gray-300 rounded focus:outline-none focus:ring focus:border-blue-300">
            </div>

            <div class="mb-4">
                <label for="campaignName" class="block text-sm font-medium text-gray-700 mb-2">Campaign Name:</label>
                <input v-model="campaignName" @input="generateLink" placeholder="Campaign Name"
                    class="w-full px-4 py-2 border border-gray-300 rounded focus:outline-none focus:ring focus:border-blue-300">
            </div>

            <div id="generatedLink" class="mt-6 text-sm text-gray-700 break-words cursor-copy" @click="copyLink">{{
                generatedLink }}</div>
            <button
                class="mt-2 px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 focus:outline-none  focus:border-blue-300"
                :class="{ 'bg-green-500 hover:bg-green-600': copied }" @click="copyLink">{{ copied ? "Copied" : "Copy" }}
            </button>

        </div>
    </div>
</template>

<script>
export default {
    name: 'LinkingTool',
    data() {
        return {
            website: '',
            campaignId: '',
            campaignSource: '',
            campaignMedium: '',
            campaignName: '',
            generatedLink: '',
            copied: false //  default is false, after copy is true
        };
    },
    methods: {
        generateLink() {
            this.generatedLink = `${this.website}?utm_source=${this.campaignSource.replace(/\s/g, '+')}&utm_medium=${this.campaignMedium.replace(/\s/g, '+')}&utm_campaign=${this.campaignName.replace(/\s/g, '+')}&utm_id=${this.campaignId.replace(/\s/g, '+')}`;
        },
        copyLink() {
            if (navigator.clipboard) {//for browser supports clipboard api
                navigator.clipboard.writeText(this.generatedLink)
                    .then(() => {
                        this.copied = true;
                        setTimeout(() => {
                            this.copied = false;
                        }, 3000); // Hide after 3 seconds
                    })
                    .catch((error) => {
                        console.error('Failed to copy link:', error);
                    });
            } else {
                // for older browsers
                const textarea = document.createElement('textarea');
                textarea.value = this.generatedLink;
                document.body.appendChild(textarea);
                textarea.select();
                try {
                    document.execCommand('copy');
                    this.copied = true;
                    setTimeout(() => {
                        this.copied = false;
                    }, 3000); // Hide after 3 seconds
                } catch (error) {
                    console.error('Failed to copy link:', error);
                }
                document.body.removeChild(textarea);
            }
        }

    }
}
</script>

<style lang="scss" scoped></style>
