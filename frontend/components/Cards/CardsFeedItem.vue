<template>
  <div
    class="rounded-md bg-light-header dark:bg-dark-header border border-light-section-div dark:border-dark-section-div p-2 sm:p-3"
  >
    <div class="flex items-center space-x-3">
      <Icon v-if="(item.itemType = 'group')" name="bi:people" size="1.5em" />
      <Icon
        v-else-if="item.url.includes('mastodon')"
        name="bi:mastodon"
        size="1.5em"
      />
      <Icon
        v-else-if="item.url.includes('twitter')"
        name="bi:twitter"
        size="1.5em"
      />
      <Icon
        v-else-if="item.url.includes('facebook')"
        name="bi:facebook"
        size="1.5em"
      />
      <Icon
        v-else-if="item.url.includes('instagram')"
        name="bi:instagram"
        size="1.5em"
      />
      <h4 class="responsive-h5 font-bold">{{ item.title }}</h4>
    </div>
    <p class="pb-3">
      {{ item.description }}
    </p>
    <div
      class="w-full bg-light-placeholder dark:bg-dark-placeholder h-32 rounded-md"
    >
      <img :src="item.imgURL" alt="" class="" />
    </div>
  </div>
</template>

<script setup lang="ts">
import type { FeedItem } from "../../types/feedItem";

const props = defineProps<{
  url: string;
}>();

let itemType: string = "";
if (props.url.includes("activist")) {
  itemType = "group";
} else {
  itemType = "social post";
}

const item: FeedItem = {
  url: props.url,
  itemType: itemType,
  title: "Title",
  description: "Lorem ipsum dolor sit amet",
};
</script>
