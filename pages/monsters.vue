<template>
    <div>
        <section class="info3 cid-siZ6QBt3X3" id="info3-n">



            <div class="mbr-overlay" style="opacity: 0.6; background-color: rgb(68, 121, 217);">
            </div>
            <div class="container-fluid">
                <div class="row justify-content-center">
                    <div class="card col-12 col-lg-10">
                        <div class="card-wrapper">
                            <div class="card-box align-center">
                                <h4 class="card-title mbr-fonts-style align-center mb-4 display-1">
                                    <strong>Monsters</strong></h4>
                                <p class="mbr-text mbr-fonts-style mb-4 display-7">
                                    Hundreds of monsters from dragons to spirit beasts</p>

                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="features3 cid-siZ6P35no1" id="features3-m">


            <div class="container">

                <div class="row mt-4">
                  <div class="col-12 col-lg-6" v-for="characters in monsters" :key="characters">
                        <div class="image-wrapper">
                            <characters :character="characters" />
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script setup>
import characters from '~/components/Related/character.vue';
  const {
        $directus,
        $readItems
    } = useNuxtApp()

    const {
        data: monsters
    } = await useAsyncData('monsters', () => {
        return $directus.request($readItems('characters', {
            filter: {
                type: {
                    _eq: "Kids"
                },
                tags: {
                  tags_id: {
                    name: {
                      _eq: "Monsters"
                    }
                  }
                }
            }
        }))
    })

    useHead({
      title: 'Monsters'
    })
</script>