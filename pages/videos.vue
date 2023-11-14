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

                <div class="row mbr-gallery mt-4">
                    <div class="col-12 col-md-6 col-lg-3 item gallery-image" v-for="videos in data.VideoItems.items" :key="videos">
                        <div class="item-wrapper" data-toggle="modal" data-target="#svordVMBDg-modal">
                            <img class="w-100" :src="`${videos.content.video.filename}`" :alt="videos.content.name" data-slide-to="0"
                                data-target="#lb-svordVMBDg">
                            <div class="icon-wrapper">
                                <span class="mobi-mbri mobi-mbri-search mbr-iconfont mbr-iconfont-btn"></span>
                            </div>
                        </div>
                        <h6 class="mbr-item-subtitle mbr-fonts-style align-center mb-2 mt-2 display-7">
                            <a href="#" class="text-primary">{{ videos.content.name }}</a>
                        </h6>
                    </div>
                </div>

                <div class="modal mbr-slider" tabindex="-1" role="dialog" aria-hidden="true" id="svordVMBDg-modal" v-for="videos in data.VideoItems.items" :key="videos">
                    <div class="modal-dialog" role="document">
                        <div class="modal-content">
                            <div class="modal-body">
                                <div class="carousel slide carousel-fade" id="lb-svordVMBDg" data-ride="carousel"
                                    data-interval="5000">
                                    <div class="carousel-inner">
                                        <div class="carousel-item active">
                                            <img class="d-block w-100" :src="`${videos.content.video.filename}`" :alt="videos.content.name">
                                        </div>
                                    </div>
                                    <ol class="carousel-indicators">
                                        <li data-slide-to="0" class="active" data-target="#lb-svordVMBDg"></li>
                                        <li data-slide-to="1" data-target="#lb-svordVMBDg"></li>
                                        <li data-slide-to="2" data-target="#lb-svordVMBDg"></li>
                                        <li data-slide-to="3" data-target="#lb-svordVMBDg"></li>
                                    </ol>
                                    <a role="button" href="" class="close" data-dismiss="modal" aria-label="Close">
                                    </a>
                                    <a class="carousel-control-prev carousel-control" role="button" data-slide="prev"
                                        href="#lb-svordVMBDg">
                                        <span class="mobi-mbri mobi-mbri-arrow-prev" aria-hidden="true"></span>
                                        <span class="sr-only">Previous</span>
                                    </a>
                                    <a class="carousel-control-next carousel-control" role="button" data-slide="next"
                                        href="#lb-svordVMBDg">
                                        <span class="mobi-mbri mobi-mbri-arrow-next" aria-hidden="true"></span>
                                        <span class="sr-only">Next</span>
                                    </a>
                                </div>
                            </div>
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
  VideoItems {
    items {
      id
      created_at
      content {
        name
        video {
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
        title: 'Videos',
    })
</script>