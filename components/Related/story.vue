<template>
    <div>
        <div class="item-wrapper">
            <div class="item-img">
                <img :src="`${stories.content.image.filename}`" :alt="stories.content.name">
            </div>
            <div class="item-content">
                <h5 class="item-title mbr-fonts-style display-7"><strong>{{ stories.content.name }}</strong></h5>

                <p class="mbr-text mbr-fonts-style mt-3 display-7">{{ stories.created_at }}
                </p>
            </div>
            <div class="mbr-section-btn item-footer mt-2"><a :href="`/character/${stories.id}`"
                    class="btn btn-primary item-btn display-7" target="_blank">Learn More
                    &gt;</a></div>
        </div>
    </div>
</template>

<script setup>
    const props = defineProps({
        story: {
            type: Object,
            required: true,
        },
    });
    const {
        story
    } = props;
</script>