<template>
    <div>
        <section class="info3 cid-sghqxkIegV" id="info3-9">



            <div class="mbr-overlay" style="opacity: 0.6; background-color: rgb(68, 121, 217);">
            </div>
            <div class="container">
                <div class="row justify-content-center">
                    <div class="card col-12 col-lg-10">
                        <div class="card-wrapper">
                            <div class="card-box align-center">
                                <h4 class="card-title mbr-fonts-style align-center mb-4 display-1">
                                    <strong>Stories</strong></h4>


                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="content2 cid-sghqCAf7ii" id="content2-a">


            <div class="container-fluid">

                <div class="row mt-4">
                    <div class="item features-image сol-12 col-md-6 col-lg-4" v-for="stories in stories" :key="stories">
                        <story :story="stories" />
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
    export default {

    }
</script>

<script setup>
import story from '~/components/Related/story.vue';

const {
      $directus,
      $readItems
  } = useNuxtApp()

  const {
      data: stories
  } = await useAsyncData('stories', () => {
      return $directus.request($readItems('stories', {
          filter: {
              status: {
                  _eq: "Kids"
              }
          }
      }))
  })

    useHead({
        title: 'Stories',
    })
</script>