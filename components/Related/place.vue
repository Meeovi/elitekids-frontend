<template>
  <div>
    <a :href="`/places/${place?.slug}`">
      <div class="item-wrapper">
        <div class="item-img">
          <img :src="`${places.content.image.filename}`" :alt="places.content.name">
        </div>
        <div class="item-content">
          <h5 class="item-title mbr-fonts-style display-7"><strong>{{ places.content.name }}</strong></h5>

          <p class="mbr-text mbr-fonts-style mt-3 display-7">{{ places.content.location.name }}
          </p>
        </div>
        <div class="mbr-section-btn item-footer mt-2"><a :href="`/character/${places.id}`"
            class="btn btn-primary item-btn display-7" target="_blank">Learn More
            &gt;</a></div>
      </div>
    </a>
  </div>
</template>

<script setup>
  const props = defineProps({
    place: {
      type: Object,
      required: true,
    },
  });
  const {
    place
  } = props;
</script>