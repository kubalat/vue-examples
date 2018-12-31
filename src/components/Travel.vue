<template>
    <span><strong>Name: </strong>{{ travel.name }} <strong> Price: </strong>{{ travel.price }}</span>
</template>


<script>


export default {
  name: 'Travel',

  props: {
    travel: Object
  }
}
</script>
