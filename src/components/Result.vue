<template>
  <div class="container" @click="closeModal">
      <div class="modal">
            <h3>your time was: {{score}}</h3>
            <h4>{{range}}</h4>
      </div>
  </div>
</template>

<script>
import { onMounted, ref } from '@vue/runtime-core'
export default {
    props: {
        score: null,
    },
    emits: ["closeResult"],
    setup(props, {emit}){
        const grade =  ref(["That Was Lightening Fast", "Nice One Quick Draw", "Fast Enough..", "Damn, My GrandMa is Faster Than That.."])
        let range = ref('')
        

        onMounted( () => {
            props.score ? console.log("on mounted exist"): null
            if (props.score < 250) {
            range.value = grade.value[0]
        } else if(props.score < 550) {
            range.value = grade.value[1]
        }
        else if (props.score < 1150){
            range.value = grade.value[2]
        }
        else{
            range.value = grade.value[3]
        }
        })

        function closeModal(){
            emit('closeResult')
        }

        return {range, closeModal}
    }
}
</script>

<style scoped>
.container {
  position: absolute;
  top: 0;
  background-color: rgba(230, 230, 230, 0.5);
  width: 100%;
  height: 100%;
  z-index: 1;
}

.modal {
  background: tomato;
  width: 45%;
  padding: 4rem;
  margin: 10rem auto;
  z-index: 10 !important;
  opacity: 1 !important;
} 
</style>