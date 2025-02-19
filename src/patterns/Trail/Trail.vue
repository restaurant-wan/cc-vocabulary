<template>
  <div class="vocab trail" :class="trailClasses">
    <ul class="crumbs">
      <li
        v-for="(trailCrumb, index) in trailCrumbList"
        :key="index"
        class="crumb">
        <span
          v-for="loop in index"
          :key="loop"
          class="spacing">
          <template v-if="loop === index">↳</template>
        </span>
        <a :href="trailCrumb.link">
          <SlotRenderer
            :component="trailCrumb"
            name="addons"
            tag="span">
            <FontAwesomeIcon
              v-if="trailCrumb.icon"
              :icon="['fas', trailCrumb.icon]"
              fixed-width/>
          </SlotRenderer>
          <SlotRenderer
            :component="trailCrumb"
            tag="span"/>
        </a>
        <FontAwesomeIcon
          class="separator"
          :icon="['fas', icon]"
          fixed-width/>
      </li>
    </ul>
    <div v-show="false">
      <!-- @slot [`TrailCrumb`](#/Patterns/TrailCrumb) components go here -->
      <slot/>
    </div>
  </div>
</template>

<script>
  import { library } from '@fortawesome/fontawesome-svg-core'
  import { faAngleRight } from '@fortawesome/free-solid-svg-icons'
  import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

  import SlotRenderer from '@/utils/SlotRenderer/SlotRenderer'

  import Colored from '@/mixins/colored'
  import Invertible from '@/mixins/invertible'

  library.add(faAngleRight)

  /**
   * ### Trail crumbs help you go back.
   *
   * Trail provides a collection of
   * [TrailCrumb](#/Patterns/TrailCrumbs)s in a familiar interface to
   * facilitate exploration.
   */
  export default {
    name: 'Trail',
    mixins: [
      Colored,
      Invertible
    ],
    provide: function () {
      return {
        trailCrumbList: this.trailCrumbList
      }
    },
    components: {
      SlotRenderer,
      FontAwesomeIcon
    },
    props: {
      /**
       * _the icon to use as the separator between crumbs_
       */
      icon: {
        type: String,
        default: 'angle-right'
      }
    },
    data: function () {
      return {
        trailCrumbList: []
      }
    },
    computed: {
      trailClasses: function () {
        return [
          ...this.coloredClasses,
          ...this.invertibleClasses
        ]
      }
    }
  }
</script>

<style lang="stylus" src="./Trail.styl">
</style>
