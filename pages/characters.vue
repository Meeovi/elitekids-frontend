<template>
    <div>
        <section class="info3 cid-sgjsdXQPPM" id="info3-i">



            <div class="mbr-overlay" style="opacity: 0.6; background-color: rgb(68, 121, 217);">
            </div>
            <div class="container-fluid">
                <div class="row justify-content-center">
                    <div class="card col-12 col-lg-10">
                        <div class="card-wrapper">
                            <div class="card-box align-center">
                                <h4 class="card-title mbr-fonts-style align-center mb-4 display-1">
                                    <strong>Characters</strong></h4>


                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="image4 cid-sgjsafsZOP" id="image4-h">
            <div class="container">
                <div class="row">
                    <div class="col-12 col-lg-6" v-for="characters in charactersData" :key="characters">
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
        data: charactersData
    } = await useAsyncData('charactersData', () => {
        return $directus.request($readItems('characters', {
            filter: {
                status: {
                    _eq: "Kids"
                }
            }
        }))
    })

    useHead({
      title: 'Characters'
    })
</script>