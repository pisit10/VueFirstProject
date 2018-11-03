<template>
    <div>
        <Button @click="sendText" type="button" class="btn btn-info">
           <span :class="icon"></span> {{name}}
        </Button>
    </div>
</template>

<script>
export default {
  name: 'ButtonIcon',
  props: {
    icon: {
        type: String,
        default : "fa fa-search" 
    },
    name:{
        type: String,
        default : "Click Me"
    }
  },
  methods: {
      sendText() {
          this.$emit('buttonText',20)
      }
  },
}
</script>

<style scoped>
</style>