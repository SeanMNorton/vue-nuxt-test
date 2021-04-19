<template>
  <div class="card" :class="isPortrait ? 'portrait' : 'landscape'">
    <div class="image">
      <slot name="image" />
    </div>

    <div class="content">
      <slot name="content" />
    </div>

    <div class="footer">
      <slot name="footer" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    isPortrait: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped>
 .card {
  display: flex;
  flex-direction: row;
  justify-content: center;
  box-shadow: 2px 2px 5px lightgrey;
  border-radius: 8px;
  overflow: hidden;
 }
 .content {
   padding: 10px 10px;
 }
 .footer {
   padding: 10px 10px;
 }
 .card.portrait {
  flex-direction: column;
 }
 .card.landscape {
   flex-direction: row;
 }
</style>
