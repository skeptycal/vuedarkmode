<!-- *************************************************************************
     TEMPLATE
     ************************************************************************* -->

<template lang="pug">
.c-guide-base-dividers
  div(
    v-if="!documentation"
    class="c-guide-base-dividers__showroom o-elements"
  )
    div(
      v-for="(color, i) in dividers.colors"
      :key="'divider' + color + i"
      class="o-elements__category"
    )
      div(
        v-for="(size, j) in dividers.sizes"
        :key="'divider' + color + j + size"
        class="o-elements__item"
      )
        base-divider(
          :color="color"
          :size="size"
          class="c-guide-base-dividers__divider"
        )

  div(
    v-else
    class="c-guide-base-dividers__documentation"
  )
    pre(v-highlightjs)
      code(class="html")
        | &lt;!-- Insert this component in your code --&gt;
        | &lt;!-- Customize it with props (see table below) --&gt;
        | &lt;dm-divider&gt;&lt;/dm-divider&gt;

    no-ssr
      common-table(
        :data="props.data"
        :fields="props.fields"
      )
</template>

<!-- *************************************************************************
     SCRIPT
     ************************************************************************* -->

<script>
// VUE DARK MODE
import BaseDivider from "@/../lib/components/base/BaseDivider";

// PROJECT
const CommonTable = () => import("@/components/common/CommonTable");

export default {
  components: {
    BaseDivider,
    CommonTable
  },

  props: {
    documentation: {
      type: Boolean,
      default: false
    }
  },

  data() {
    return {
      dividers: {
        colors: [
          "blue",
          "green",
          "red",
          "orange",
          "turquoise",
          "purple",
          "black",
          "white"
        ],
        sizes: ["large", "small"]
      },
      props: {
        fields: [
          {
            name: "name",
            title: "Prop Name",
            dataClass: "u-bold",
            width: "150px"
          },
          {
            name: "type",
            title: "Type",
            width: "150px"
          },
          {
            name: "details",
            title: "Details"
          }
        ],
        data: [
          {
            name: "color",
            type: {
              type: "String",
              additional: 'Default: "black"'
            },
            details: {
              description: "Specify the color of the divider.",
              values:
                '"black" | "blue" | "green" | "orange" | "purple" | "red" | "turquoise" | "white"'
            }
          },
          {
            name: "margin",
            type: {
              type: "String",
              additional: "Default: null"
            },
            details: {
              description: "Specify the margin of the divider."
            }
          },
          {
            name: "size",
            type: {
              type: "String",
              additional: 'Default: "large"'
            },
            details: {
              description: "Specify the size of the divider.",
              values: '"small" | "large"'
            }
          }
        ]
      }
    };
  }
};
</script>

<!-- *************************************************************************
     STYLE
     ************************************************************************* -->

<style lang="scss">
// VARIABLES
$c: ".c-guide-base-dividers";

#{$c} {
  #{$c}__showroom {
    grid-gap: 20px;
    grid-template-columns: repeat(auto-fill, 100%);
    margin-bottom: 0;

    #{$c}__divider {
      margin: 0 auto !important;
    }
  }
}
</style>
