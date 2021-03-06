<template>
  <div @click="Show">
    <div
        v-if="$slots.popover"
        :class="[Position]"
        class="popover"
        ref="parent"
    >
      <slot name="popover"></slot>

      <transition
          :duration="{ enter: 300, leave: 300 }"
          name="fade"
          @enter="Enter"
      >
        <div v-show="isShow">
          <div class="popover-overlay"
               @click.stop="Hide"
          ></div>

          <div ref="popover"
               class="popover-item"
          >
            <div class="popover--content">
              <slot></slot>
            </div>
            <div class="popover-tip"></div>
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
    const BaseClass = "popover--";
    const PopoverPosition = {
        top: BaseClass + 'top',
        bottom: BaseClass + 'bottom',
        right: BaseClass + 'right',
        left: BaseClass + 'left',
    };

    export default {
        name: "vue-popover",
        props: {
            placement: {
                type: String,
                default: 'top'
            },
            offset: {
                type: Number,
                default: 15
            },
        },
        data: () => ({
            isShow: false,
        }),
        computed: {
            Position() {
                return PopoverPosition[this.placement];
            },
        },
        methods: {
            Show() {
                this.isShow = true;
            },
            Hide() {
                this.isShow = false;
            },
            Enter() {
                const content = this.$slots.popover[0].elm
                const popover = this.$refs.popover
                const offset = this.offset
                const contentWidth = content.offsetWidth;
                const contentHeight = content.offsetHeight;

                switch (this.placement) {
                    case 'top':
                        popover.style.left = (contentWidth / 2) - (popover.offsetWidth / 2) + 'px';
                        popover.style.top = -this.$refs.popover.offsetHeight - contentHeight + 'px';
                        break;
                    case 'left':
                        popover.style.left = -popover.offsetWidth - offset + 'px';
                        popover.style.top = (contentHeight / 2) - (popover.offsetHeight / 2) + 'px';
                        break;
                    case 'right':
                        popover.style.left = contentWidth + offset + 'px';
                        popover.style.top = (contentHeight / 2) - (popover.offsetHeight / 2) + 'px';
                        break;
                    case 'bottom':
                    default:
                        popover.style.left = (contentWidth / 2) - (popover.offsetWidth / 2) + 'px';
                        popover.style.top = contentHeight + offset + 'px';
                        break;
                }
            },
        }
    }
</script>

<style scoped lang="scss">
  @import './popover';
</style>