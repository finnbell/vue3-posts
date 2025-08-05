<template>
  <div>
    <h2>게시글 목록</h2>
     <h4 class="my-4"></h4>
     <div class="row g-3">
      <div v-for="post in posts" :key="post.id" class="col-4">
        <PostItem
        :title="post.title"
        :content="post.content"
        :created-at="post.createdAt"
        @click="goPage(post.id)"
        ></PostItem>
      </div>
     </div>
     <hr class="my-4"/>
    <AppCard>
      <PostDetailView :id="1"></PostDetailView>
    </AppCard>
  </div>
</template>

<script setup>
import PostItem from '@/components/posts/PostItem.vue'
import PostDetailView from '@/views/posts/PostDetailView.vue'
import AppCard from '@/components/AppCard.vue'

import { getPosts } from '@/api/posts'
import { ref } from 'vue'
import { useRouter } from 'vue-router';
import AppCardVue from '../../components/AppCard.vue'
const router = useRouter();
const posts = ref([]);


const fetchPosts = () => {
  posts.value = getPosts();
};
fetchPosts();

const goPage = (id) => {
  //router.push(`/posts/${id}`)
  //http://localhost:5173/posts/1?searchText=hello#world!  이렇게 url 이 생성됨 
  router.push({
    name:'PostDetail',
    params: {
      id,
    },
    query: {
      searchText: 'hello',
    },
    hash: '#world!',
  })
}
</script>

<style lang="scss" scoped>

</style>