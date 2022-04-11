
<template>
  <div>
    <cld-image :public-id="publicId" >
      <cld-transformation effect="blur:300"/>
      <cld-transformation :overlay="{fontFamily: 'Berkshire Swash', fontSize: 40, fontWeight: 'bold', text: title}" color="#fff" opacity="90" crop="fit" width="400" background="#000" x="-80" effect="shadow" y="-60"/>
      <cld-transformation :overlay="{fontFamily: 'Lustria', fontSize: 16, fontWeight: '', text: description}" color="#000" crop="fit" width="190" x="-200" y="35"/>
      <cld-transformation :overlay="{fontFamily: 'Lustria', fontSize: 15, fontWeight: 'bold', text: `Speakers: ${speakers}`}" color="#fff" effect="shadow"  crop="fit" width="120" background="#000" x="200" y="130"/>
    </cld-image>
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
}
</script>