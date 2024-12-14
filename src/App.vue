<template>
  <div class="min-h-screen bg-gray-200 flex flex-col items-center">
    <header class="w-full bg-blue-600 text-white p-4 text-center shadow-md">
      <h1 class="text-4xl font-extrabold">YouTube Proxy Viewer</h1>
    </header>
    <main class="flex-grow flex flex-row w-full max-w-7xl mx-auto">
      <!-- Left Ad Section -->
      <aside class="hidden md:block w-1/5 bg-gray-100 p-4 border-r border-gray-300">
        <h2 class="text-lg font-semibold mb-4">Advertisements</h2>
        <div class="h-64 bg-gray-300 mb-4 rounded">Ad Space</div>
        <div class="h-64 bg-gray-300 rounded">Ad Space</div>
      </aside>

      <!-- Main Content -->
      <section class="flex-grow bg-white p-6 shadow-md rounded-md mx-4">
        <h2 class="text-2xl font-bold text-blue-500 mb-4 text-center">Watch Videos Anonymously</h2>
        <form @submit.prevent="fetchVideo" class="flex w-full max-w-md mx-auto">
          <input
            type="text"
            v-model="youtubeUrl"
            placeholder="Enter YouTube Video URL"
            class="flex-grow p-2 border border-gray-300 rounded-l-md focus:outline-none focus:ring focus:border-blue-300"
          />
          <button
            type="submit"
            class="bg-blue-500 text-white p-2 rounded-r-md hover:bg-blue-600 focus:outline-none"
          >
            Watch
          </button>
        </form>
        <div v-if="videoUrl" class="mt-6 w-full max-w-3xl mx-auto">
          <video
            controls
            :src="videoUrl"
            class="w-full border border-gray-300 rounded-md shadow-md"
          ></video>
        </div>
        <p v-if="errorMessage" class="text-red-500 mt-4 text-center">{{ errorMessage }}</p>
      </section>

      <!-- Right Ad Section -->
      <aside class="hidden md:block w-1/5 bg-gray-100 p-4 border-l border-gray-300">
        <h2 class="text-lg font-semibold mb-4">Advertisements</h2>
        <div class="h-64 bg-gray-300 mb-4 rounded">Ad Space</div>
        <div class="h-64 bg-gray-300 rounded">Ad Space</div>
      </aside>
    </main>
    <footer class="w-full bg-gray-800 text-white text-center p-4">
      <p class="mt-1">This WebApp was developed by Alireza shahbaziyan.</p>
      <div class="flex justify-center space-x-4 mt-2">
        <a
          href="https://www.linkedin.com/in/your-linkedin-username"
          target="_blank"
          class="text-blue-400 hover:underline"
        >
          LinkedIn
        </a>
        <a
          href="https://github.com/your-github-username"
          target="_blank"
          class="text-blue-400 hover:underline"
        >
          GitHub
        </a>
      </div>
    </footer>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    const youtubeUrl = ref<string>('');
    const videoUrl = ref<string | null>(null);
    const errorMessage = ref<string>('');

    const fetchVideo = async () => {
      errorMessage.value = '';
      videoUrl.value = null;

      if (!youtubeUrl.value) {
        errorMessage.value = 'Please enter a valid YouTube URL.';
        return;
      }

      try {
        const response = await fetch('https://your-backend-domain.com/api/proxy', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({ url: youtubeUrl.value }),
        });

        if (!response.ok) {
          throw new Error('Failed to fetch video');
        }

        const data = await response.json();
        videoUrl.value = data.videoUrl;
      } catch (error) {
        errorMessage.value = 'Could not fetch video. Please try again.';
      }
    };

    return {
      youtubeUrl,
      videoUrl,
      errorMessage,
      fetchVideo,
    };
  },
});
</script>

<style scoped>
body {
  @apply bg-gray-200;
}
</style>
