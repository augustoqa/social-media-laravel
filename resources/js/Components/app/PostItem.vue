<script setup>
import {
  Disclosure,
  DisclosureButton,
  DisclosurePanel
} from '@headlessui/vue'

defineProps({
  post: Object
})

function isImage(attachment) {
  const mime = attachment.mime.split('/')
  return mime[0].toLowerCase() === 'image'
}
</script>

<template>
  <div class="bg-white border rounded p-4 shadow mb-3">
    <div class="flex items-center gap-2 mb-3">
      <a href="javascript:void(0)">
        <img :src="post.user.avatar"
             class="w-[42px] rounded-full border border-b-2 transition-all hover:border-blue-500">
      </a>
      <div>
        <h4 class="font-bold">
          <a class="hover:underline" href="javascript:void(0)">
            {{ post.user.name }}
          </a>
          <template v-if="post.group">
            >
            <a class="hover:underline" href="javascript:void(0)">
              {{ post.group.name }}
            </a>
          </template>
        </h4>
        <small class="text-gray-400">{{ post.created_at }}</small>
      </div>
    </div>
    <div class="mb-3">
      <Disclosure v-slot="{ open }">
        <div v-if="!open" v-html="post.body.substring(0, 200) + '...'"></div>
        <DisclosurePanel v-else>
          <div v-html="post.body" />
        </DisclosurePanel>
        <div class="flex justify-end">
          <DisclosureButton class="text-blue-500 hover:underline">
            {{ open ? 'Read less' : 'Read More' }}
          </DisclosureButton>
        </div>
      </Disclosure>
    </div>
    <div class="grid grid-cols-2 lg:grid-cols-3 gap-3 mb-3">
      <div v-for="attachment of post.attachments">
        <div
          class="group bg-blue-100 flex flex-col items-center justify-center gap-2 relative text-gray-500 h-full">
          <button
            class="bg-gray-600 hover:bg-gray-700 absolute right-3 top-3 p-2 cursor-pointer rounded-full text-white transition-all opacity-0 group-hover:opacity-100">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                 stroke="currentColor" class="w-5 h-5">
              <path stroke-linecap="round" stroke-linejoin="round"
                    d="M3 16.5v2.25A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75V16.5M16.5 12 12 16.5m0 0L7.5 12m4.5 4.5V3" />
            </svg>
          </button>

          <img v-if="isImage(attachment)" :src="attachment.url" class="max-w-full w-auto">

          <template v-else>
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                 stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                    d="M19.5 14.25v-2.625a3.375 3.375 0 0 0-3.375-3.375h-1.5A1.125 1.125 0 0 1 13.5 7.125v-1.5a3.375 3.375 0 0 0-3.375-3.375H8.25m2.25 0H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125V11.25a9 9 0 0 0-9-9Z" />
            </svg>

            <small>{{ attachment.name }}</small>
          </template>
        </div>
      </div>
    </div>
    <div class="flex gap-2">
      <button
        class="text-gray-800 flex gap-1 items-center py-2 px-4 justify-center bg-gray-100 hover:bg-gray-200 transition-all rounded-lg flex-1">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
             class="w-6 h-6">
          <path stroke-linecap="round" stroke-linejoin="round"
                d="M6.633 10.25c.806 0 1.533-.446 2.031-1.08a9.041 9.041 0 0 1 2.861-2.4c.723-.384 1.35-.956 1.653-1.715a4.498 4.498 0 0 0 .322-1.672V2.75a.75.75 0 0 1 .75-.75 2.25 2.25 0 0 1 2.25 2.25c0 1.152-.26 2.243-.723 3.218-.266.558.107 1.282.725 1.282m0 0h3.126c1.026 0 1.945.694 2.054 1.715.045.422.068.85.068 1.285a11.95 11.95 0 0 1-2.649 7.521c-.388.482-.987.729-1.605.729H13.48c-.483 0-.964-.078-1.423-.23l-3.114-1.04a4.501 4.501 0 0 0-1.423-.23H5.904m10.598-9.75H14.25M5.904 18.5c.083.205.173.405.27.602.197.4-.078.898-.523.898h-.908c-.889 0-1.713-.518-1.972-1.368a12 12 0 0 1-.521-3.507c0-1.553.295-3.036.831-4.398C3.387 9.953 4.167 9.5 5 9.5h1.053c.472 0 .745.556.5.96a8.958 8.958 0 0 0-1.302 4.665c0 1.194.232 2.333.654 3.375Z" />
        </svg>
        Like
      </button>
      <button
        class="text-gray-800 flex gap-1 items-center py-2 px-4 justify-center bg-gray-100 hover:bg-gray-200 transition-all rounded-lg flex-1">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
             class="w-6 h-6">
          <path stroke-linecap="round" stroke-linejoin="round"
                d="M8.625 12a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0H8.25m4.125 0a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0H12m4.125 0a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0h-.375M21 12c0 4.556-4.03 8.25-9 8.25a9.764 9.764 0 0 1-2.555-.337A5.972 5.972 0 0 1 5.41 20.97a5.969 5.969 0 0 1-.474-.065 4.48 4.48 0 0 0 .978-2.025c.09-.457-.133-.901-.467-1.226C3.93 16.178 3 14.189 3 12c0-4.556 4.03-8.25 9-8.25s9 3.694 9 8.25Z" />
        </svg>

        Comment
      </button>
    </div>
  </div>
</template>

<style scoped>

</style>
