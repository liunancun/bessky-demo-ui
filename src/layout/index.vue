<template>
  <div class="layout" :class="{'hide-sidebar':!sidebar.opened}">
    <sidebar />
    <div class="right">
      <navbar />
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import Sidebar from './components/Sidebar'
import Navbar from './components/Navbar'

export default {
  name: 'Layout',
  components: { Sidebar, Navbar },
  computed: {
    ...mapGetters(['sidebar'])
  }
}
</script>

<style lang="scss" scoped>
.layout > .right {
  margin-left: 210px;
}

.hide-sidebar > .right {
  margin-left: 64px;
}
</style>