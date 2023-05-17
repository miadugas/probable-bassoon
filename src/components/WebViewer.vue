<template>
  <div class="viewer-container">
    <div id="webviewer" ref="viewer"></div>
  </div>
</template>

<script lang="ts">
	import { ref, onMounted, nextTick } from 'vue'
	import WebViewer from '@pdftron/webviewer'

	export default {
	  name: 'WebViewer',
	  props: { initialDoc: { type: String }},
	  setup(props) {
	    const viewer = ref<HTMLElement | null>(null)
	    onMounted(() => {
	      nextTick().then(() => {
	        if (viewer.value) {
	          const path = `${import.meta.env.BASE_URL}webviewer`;
	          WebViewer({ path, initialDoc: props.initialDoc }, viewer.value);
	        }
	      })
	    })
	    return { viewer }
	  },
	}
</script>

<style>
.viewer-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
  padding: 5px; /* This will act as a margin around the webviewer */
  box-sizing: border-box;
}

#webviewer {
  height: 100%;
  width: 100%;
  box-sizing: border-box;
  padding: 5px;

}

@media (max-width: 768px) {
  #webviewer {
    height: calc(80vh - 20px);
    width: calc(90vw - 20px);
    padding: 5px;
  }
}

</style>
