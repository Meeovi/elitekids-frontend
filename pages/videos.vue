<template>
    <div>
        <section class="info3 cid-sghrK4qopH" id="info3-d">
            <div class="mbr-overlay" style="opacity: 0.6; background-color: rgb(68, 121, 217);">
            </div>
            <div class="container">
                <div class="row justify-content-center">
                    <div class="card col-12 col-lg-10">
                        <div class="card-wrapper">
                            <div class="card-box align-center">
                                <h4 class="card-title mbr-fonts-style align-center mb-4 display-1">
                                    <strong>Elite TV</strong></h4>


                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="gallery5 mbr-gallery cid-sghrLMhsMk" id="gallery5-e">
            <div class="container-fluid">
                <v-card color="white" :class="['ma-4', selectedClass]" height="320" width="350">
              <video :src="`$${videos?.video?.filename_disk}`" controls height="250" width="350"></video>
              <v-card-title>{{ videos?.name }}</v-card-title>
            </v-card>
            </div>
        </section>
    </div>
</template>

<script setup>
  const {
        $directus,
        $readItems
    } = useNuxtApp()

    const {
        data: videos
    } = await useAsyncData('videos', () => {
        return $directus.request($readItems('videos', {
          filter: {
              status: {
                  _eq: "Kids"
              }
          }
      }))
  })

  useHead({
    title: 'Videos',
  })
</script>