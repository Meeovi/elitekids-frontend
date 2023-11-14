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
                    <div class="item features-image сol-12 col-md-6 col-lg-4" v-for="stories in data.StoryItems.items" :key="stories">
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
const query = gql `
query {
  StoryItems {
    items {
      id
      created_at
      content {
        name
        excerpt
        description
        image {
          filename
        }
      }
    }
  }
}
`

  const {
    data
  } = await useAsyncQuery(query)

    useHead({
        title: 'Stories',
    })
</script>