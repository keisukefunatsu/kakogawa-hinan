<template>
  <l-marker :lat-lng="position" :title="title" :draggable="false">
    <!-- <l-popup :content="text"></l-popup> -->
  </l-marker>
</template>

<script>
import { LMarker, LPopup } from "nuxt-leaflet";
export default {
  name: "MarkerPopup",
  components: {
    LMarker,
    LPopup
  },
  props: ["text", "position", "title"]
};
</script>