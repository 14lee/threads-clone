<script setup lang="ts">
import MainLayout from '~/layouts/MainLayout.vue';
import { useUserStore } from '~/stores/user';

const userStore = useUserStore();

const posts = ref<{
  name: string;
  image: string;
  text: string;
  picture: string;
}[]>([]);
const isPosts = ref(true);
const isLoading = ref(false);

onBeforeMount(() => {
  posts.value = [
    {
      name: 'Post 1',
      image: 'https://via.placeholder.com/150',
      text: 'Lorem ipsum dolor sit amet.',
      picture: 'https://via.placeholder.com/500',
    }
  ]
})
</script>

<template>
  <MainLayout>
    <div id="IndexPage" class="w-full overflow-auto">
      <div class="mx-auto max-x-[500px] overflow-hidden">
        <div id="Posts" class="px-4 max-w-[600px] mx-auto">
          <div v-if="isPosts" v-for="post in posts" :key="post.name">
            <Post :post="post" @isDeleted="posts = []"></Post>
          </div>
        </div>
      </div>
    </div>
  </MainLayout>
</template>
