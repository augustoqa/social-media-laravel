<script setup>

import PostItem from '@/Components/app/PostItem.vue'

const post1 = {
  user: {
    id: 1,
    avatar: 'https://cdn.cloudflare.steamstatic.com/steamcommunity/public/images/avatars/a0/a00b2e34559c9d5075c0efecf29ed01d34ef9129_full.jpg',
    name: 'John Smith'
  },
  group: null,
  attachments: [
    {
      id: 1,
      name: 'test.png',
      url: 'https://picsum.photos/1000',
      mime: 'image/png'
    },
    {
      id: 2,
      name: 'test2.png',
      url: 'https://picsum.photos/1000',
      mime: 'image/png'
    },
    {
      id: 3,
      name: 'MyDocument.docx',
      url: 'https://picsum.photos/1000',
      mime: 'application/msword'
    }
  ],
  body: `
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci cupiditate dignissimos, dolor ducimus eaque eos est necessitatibus neque officia placeat ratione rem sit, voluptas. Blanditiis dolorum est et hic illum.</p>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci cupiditate dignissimos, dolor ducimus eaque eos est necessitatibus neque officia placeat ratione rem sit, voluptas. Blanditiis dolorum est et hic illum.</p>
  `,
  created_at: '2023-11-19 15:12'
}

const post2 = {
  user: {
    id: 1,
    avatar: 'https://cdn.cloudflare.steamstatic.com/steamcommunity/public/images/avatars/a0/a00b2e34559c9d5075c0efecf29ed01d34ef9129_full.jpg',
    name: 'James Does'
  },
  group: {
    id: 1,
    name: 'Laravel Developers'
  },
  body: `
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci cupiditate dignissimos, dolor ducimus eaque eos est necessitatibus neque officia placeat ratione rem sit, voluptas. Blanditiis dolorum est et hic illum.</p>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci cupiditate dignissimos, dolor ducimus eaque eos est necessitatibus neque officia placeat ratione rem sit, voluptas. Blanditiis dolorum est et hic illum.</p>
  `,
  created_at: '2023-11-19 15:12'
}
</script>

<template>
  <div class="overflow-auto">
    <PostItem :post="post1" />
    <PostItem :post="post2" />
  </div>
</template>

<style scoped>

</style>
