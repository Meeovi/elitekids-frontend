<template>
    <div>
        <section class="info3 cid-sgjxq7IxV1" id="info3-k">



            <div class="mbr-overlay" style="opacity: 0.6; background-color: rgb(68, 121, 217);">
            </div>
            <div class="container">
                <div class="row justify-content-center">
                    <div class="card col-12 col-lg-10">
                        <div class="card-wrapper">
                            <div class="card-box align-center">
                                <h4 class="card-title mbr-fonts-style align-center mb-4 display-1">
                                    <strong>Places</strong></h4>


                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="content3 cid-sgjxzlY1t3" id="content3-l">


            <div class="container-fluid">

                <div class="row mt-4">
                    <div class="item features-image сol-12 col-md-6 col-lg-4" v-for="places in places" :key="places">
                        <place :place="places" />
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script setup>
import place from '~/components/Related/place.vue';

  const {
        $directus,
        $readItems
    } = useNuxtApp()

    const {
        data: places
    } = await useAsyncData('places', () => {
        return $directus.request($readItems('places', {
            filter: {
                status: {
                    _eq: "Kids"
                }
            }
        }))
    })

    useHead({
        title: 'Places',
    })
</script>