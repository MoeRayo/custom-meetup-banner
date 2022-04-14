<template>
  <div class="bg-washed-yellow vh-100">
    <header class="tc pv3 pv3-ns">
      <h1 class="tl ph5 mt2 mb0 baskerville i fw1 f2-ns f3 mid-gray ">Custom Meetup Banner Generator</h1>
    </header>
    <section class="ph5 flex flex-wrap justify-between">
      <div class="w-100 w-50-ns">
        <h2 class="baskerville fw1 f4-ns f3">Select an image</h2>

        <div v-for="banner in banners" :key="banner.id" class="fl-ns db tc pa1 grow aspect-ratio--4x6" :class="banner.id === imageId ? 'ba bw2 b--green ' : ''" @click="selectImage(banner.id, banner.publicId)">
          <cld-image :public-id="banner.publicId" crop="scale" width="150" height="100"></cld-image>
        </div>

        <p v-if="formData.error" class="cb red fw3 i f7">Please fill the required fields</p>

        <div class="mv4 cb">
          <div class="mb3 w-90">
            <label class="mb1 ttc f7 db" for="title">Title</label>
            <input id="title" v-model="formData.title" type="text" name="title" class="db w-100 pv3 ph2 br2 ba b--black-40 f7" required>
          </div>
          <div class="mb3 w-90">
            <label class="mb1 ttc f7 db" for="event-detail">event Detail</label>
            <textarea id="event-detail" v-model="formData.eventDetail" name="event-detail" class="db w-100 resize h3 ph2 pv3 f7 br2 ba b--black-40" required></textarea>
          </div>
          <div class=" w-90">
            <label class="mb1 ttc f7 db" for="speakers">Speakers</label>
            <textarea id="speakers" v-model="formData.speaker" name="speakers" class="db w-100 resize h3 ph2 pv3 f7 br2 ba b--black-40" required></textarea>
          </div>
        </div>

        <button class="f6 link dim br2 ph3 pv2 mb2 dib white bg-dark-green ba b--green pointer" @click="handleSubmit">Generate Banner</button>
      </div>
      <div class="w-100 w-50-ns pa3">
        <h2 class="baskerville fw1 f4-ns f3 underline">Result</h2>

        <div v-if="showBanner" class="mt-10">
          <GeneratedBanner
            :title="formData.title"
            :description="formData.eventDetail"
            :speakers="formData.speaker"
            :publicId="formData.publicId"
          />
        </div>

      </div>
      
    </section>
  </div>
</template>

<script>
  import banners from "~/utils/banner.json";

  export default {
    data() {
      return {
        banners,
        imageId: null,
        showBanner: false,
        formData: {
          publicId: null,
          error: false,
          title: '',
          eventDetail: '',
          speaker: ''
        }
      }
    },

  methods: {
    selectImage(imageId, publicId) {
      this.imageId = imageId
      this.formData.publicId = publicId
      this.formData.error = false
      this.showBanner = false
    },
    handleSubmit() {
      if (!this.imageId || (this.formData.title === ''|| this.formData.speaker === '')) {
        this.formData.error = true
      } else {
        this.showBanner = true 
      }
    },
  }
}
</script>

<style>
.resize {
  resize: vertical;
}
</style>