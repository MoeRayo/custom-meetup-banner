
<template>
  <div>
    <cld-image :public-id="publicId" width="1000">
      <cld-transformation crop="fit" effect="blur:100" />
      <cld-transformation effect="brightness_hsb:-50" />
      <cld-transformation
        color="#FFFFFF"
        :overlay="{
          fontFamily: 'Neucha',
          fontSize: 100,
          fontWeight: 'bold',
          text: message,
          textAlign: 'center',
        }"
        width="1300"
        crop="fit"
      />
      <cld-transformation flags="layer_apply" />
      <cld-transformation
        color="#FFFFFF"
        :overlay="{
          fontFamily: 'Dancing Script',
          fontSize: 50,
          fontWeight: 'bold',
          text: `from ${name}`,
        }"
      />
      <cld-transformation flags="layer_apply" gravity="center" x="450" y="350" />
    </cld-image>
  </div>
</template>
<script>
export default {
  props: {
    message: { type: String, required: true },
    name: { type: String, required: true },
    publicId: { type: String, required: true },
  },
}
</script>