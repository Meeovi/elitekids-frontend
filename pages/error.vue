<template>
    <div>
        <section class="header5 cid-t7W19CM5wS mbr-fullscreen mbr-parallax-background" id="header5-2">
            <div class="mbr-overlay" style="opacity: 0.2; background-color: rgb(53, 53, 53);"></div>

            <div class="container">
                <div class="row justify-content-end">
                    <div class="col-12 col-lg-7">
                        <h1 class="mbr-section-title mbr-fonts-style mbr-white mb-3 display-1"><strong>{{ page?.name }}</strong></h1>

                        <p class="mbr-text mbr-fonts-style mbr-white display-7" v-html="page?.content"></p>

                    </div>
                </div>
            </div>

            <h3 style="padding: 15px;">{{ page?.information[0]?.description }}</h3>
            <v-row>
                <v-col cols="3" v-for="characters in charactersData" :key="characters">
                    <characters :character="characters" />
                </v-col>
            </v-row>
        </section>
    </div>
</template>

<script setup>
    const {
        $directus,
        $readItems,
        $readItem
    } = useNuxtApp()
    import characters from '~/components/Related/character.vue';

    const {
        data: page
    } = await useAsyncData('page', () => {
        return $directus.request($readItem('pages', '1'))
    })

    const {
        data: charactersData
    } = await useAsyncData('charactersData', () => {
        return $directus.request($readItems('characters'))
    })

    useHead({
        title: computed(() => page?.value?.name || 'Page Name')
    })
</script>