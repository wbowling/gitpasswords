<template>
  <div :class="$style.Entries">
    <div :class="$style.Entries__List">
      <TheNav></TheNav>
    </div>
    <div :class="$style.Entries__Entry">
      <AppEntry
        v-if="entryID"
        :key="entryID"
        :entryID="entryID"
      ></AppEntry>
      <AppEntryBlank v-else></AppEntryBlank>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import AppEntry from './AppEntry'
import AppEntryBlank from './AppEntryBlank'
import TheNav from './TheNav'

export default {
  components: {
    TheNav,
    AppEntry,
    AppEntryBlank
  },

  computed: {
    ...mapGetters(['entryID'])
  }
}
</script>

<style lang="stylus" module>
@import "../styles/config.styl"

.Entries
  max-height: 100vh
  height: 100vh
  display: flex

  @media (max-width: $mobile)
    overflow: hidden
    flex-direction: column

  &__List
    @media (min-width: $tablet)
      flex: 0 0 14rem

  &__Entry
    flex: 1
    overflow-y: auto
</style>
