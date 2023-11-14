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
                    <div class="item features-image сol-12 col-md-6 col-lg-4" v-for="monsters in data.MonsterItems.items" :key="monsters">
                        <div class="item-wrapper">
                            <div class="item-img">
                                <img :src="`${monsters.content.image.filename}`" :alt="monsters.content.name">
                            </div>
                            <div class="item-content">
                                <h5 class="item-title mbr-fonts-style display-7"><strong>{{ monsters.content.name }}</strong></h5>

                                <p class="mbr-text mbr-fonts-style mt-3 display-7">{{ monsters.content.types.name }}
                                </p>
                            </div>
                            <div class="mbr-section-btn item-footer mt-2"><a :href="`/character/${monsters.id}`"
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
  MonsterItems {
    items {
      id
      content {
        name
        types {
          name
        }
        levels {
          name
        }
        affiliates {
          name
        }
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
        title: 'Monsters',
    })
</script>