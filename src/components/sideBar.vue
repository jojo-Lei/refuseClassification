<template>
    <div>
        <mp-navbar :tabs="tabs" activeIndex=0 @tabClick="tabClick"></mp-navbar>
    </div>
</template>

<script>
import mpNavbar from 'mpvue-weui/src/navbar';
export default {
  components: {
    mpNavbar,
  },
}
</script>

