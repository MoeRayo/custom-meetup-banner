
<template>
  <div>
    <cld-image ref="ref" :public-id="publicId">

      <cld-transformation effect="blur:300"/>

      <cld-transformation :overlay="{fontFamily: 'Berkshire Swash', fontSize: 40, fontWeight: 'bold', text: title}" color="#fff" opacity="90" crop="fit" width="400" background="#000" x="-80" effect="shadow" y="-60"/>

      <cld-transformation :overlay="{fontFamily: 'Lustria', fontSize: 16, fontWeight: '', text: description}" color="#000" crop="fit" width="190" x="-200" y="35"/>

      <cld-transformation :overlay="{fontFamily: 'Lustria', fontSize: 15, fontWeight: 'bold', text: `Speakers: ${speakers}`}" color="#fff" effect="shadow"  crop="fit" width="120" background="#000" x="200" y="130"/>

    </cld-image>

    <div class="mv4">
      <label class="db mb2 f3 fw4 b">Copiable link</label>
      <input disabled type="text" class="db w-90 pv3 ph2 br2 ba b--black-40 f7" :value="url" />
      <button class="f6 link dim br2 ph3 pv2 db white bg-dark-green ba b--green mt2" @click="handleCopy">{{copy}}</button>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    title: { 
      type: String, 
      required: true 
    },
    description: { 
      type: String, 
      required: true 
    },
    speakers: { 
      type: String, 
      required: true
    },
    publicId: { 
      type: String, 
      required: true
    },
  },
 data() {
    return {
      url: "",
      copy: 'Copy Link'
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.url = this.$refs.ref.$el.src
    });
  },
  methods: {
    handleCopy(){
      navigator.clipboard
      .writeText(this.url)
      .then(() => (this.copy = 'Copied!'))
      .catch((err) => err)
    }
  },
  
}
</script>