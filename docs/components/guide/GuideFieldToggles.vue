<!-- *************************************************************************
     TEMPLATE
     ************************************************************************* -->

<template lang="pug">
.c-guide-field-toggles
  div(
    v-if="!documentation"
    class="c-guide-field-toggles__showroom o-elements o-elements--form"
  )
    div(
      v-for="(statuses, i) in toggles.statuses"
      :key="'toggles ' + i"
      class="o-elements__category"
    )
      div(
        v-if="statuses[j]"
        v-for="(size, j) in toggles.sizes"
        :key="'toggles ' + i + ' ' + j"
        class="o-elements__item"
      )
        field-toggle(
          :fullWidth="false"
          :label="size.charAt(0).toUpperCase() + size.slice(1) + ' toggle (' + statuses[j] + ')'"
          :name="'toggle_' + size + '_'  + statuses[j] + i + j"
          :size="size"
          :status="statuses[j]"
          :value="i === 1"
          description="This is a customizable description for toggles."
        )

  div(
    v-else
    class="c-guide-field-toggles__documentation"
  )
    pre(v-highlightjs)
      code(class="html")
        | &lt;!-- Insert this component in your code --&gt;
        | &lt;!-- Customize it with props (see table below) --&gt;
        | &lt;dm-toggle v-model="synchronizedValue"&gt;&lt;/dm-toggle&gt;

    no-ssr
      common-table(
        :data="props.data"
        :fields="props.fields"
        class="u-mb40"
      )

    base-divider(
      class="u-mb40"
      color="white"
      size="small"
    )
    no-ssr
      common-table(
        :data="events.data"
        :fields="events.fields"
      )
</template>

<!-- *************************************************************************
     SCRIPT
     ************************************************************************* -->

<script>
// VUE DARK MODE
import BaseDivider from "@/../lib/components/base/BaseDivider";
import FieldToggle from "@/../lib/components/form/FieldToggle";

// PROJECT
const CommonTable = () => import("@/components/common/CommonTable");

export default {
  components: {
    BaseDivider,
    CommonTable,
    FieldToggle
  },

  props: {
    documentation: {
      type: Boolean,
      default: false
    }
  },

  data() {
    return {
      toggles: {
        sizes: ["large", "medium", "default", "small", "mini"],
        statuses: [
          ["normal", "normal", "normal", "normal", "normal"],
          ["normal", "success", "error", "warning"]
        ]
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
            name: "description",
            type: {
              type: "String",
              additional: "Default: null"
            },
            details: {
              description:
                "Display an helping description below the toggle element."
            }
          },
          {
            name: "disabled",
            type: {
              type: "Boolean",
              additional: "Default: false"
            },
            details: {
              description: "Disable the toggle element."
            }
          },
          {
            name: "error",
            type: {
              type: "String",
              additional: "Default: null"
            },
            details: {
              description:
                "Specify an error message to display below the toggle element."
            }
          },
          {
            name: "full-width",
            type: {
              type: "Boolean",
              additional: "Default: true"
            },
            details: {
              description:
                "When set to true, the toggle element will take all the width available."
            }
          },
          {
            name: "info",
            type: {
              type: "String",
              additional: "Default: null"
            },
            details: {
              description:
                "Specify an info message to display below the toggle element."
            }
          },
          {
            name: "label",
            type: {
              type: "String",
              additional: "Default: null"
            },
            details: {
              description: "Add a label above the toggle element."
            }
          },
          {
            name: "name",
            type: {
              type: "String",
              additional: "Required: true"
            },
            details: {
              description: "Specify the name of the toggle element."
            }
          },
          {
            name: "required",
            type: {
              type: "Boolean",
              additional: "Default: false"
            },
            details: {
              description:
                "Sets whether the toggle element must be checked before submitting the form."
            }
          },
          {
            name: "size",
            type: {
              type: "String",
              additional: 'Default: "default"'
            },
            details: {
              description: "Specify the size of the toggle element.",
              values: '"mini" | "small"  | "default" | "medium" | "large"'
            }
          },
          {
            name: "status",
            type: {
              type: "String",
              additional: 'Default: "normal"'
            },
            details: {
              description: "Specify the status for the toggle element.",
              values: '"error" | "normal" | "success" | "warning"'
            }
          },
          {
            name: "success",
            type: {
              type: "String",
              additional: "Default: null"
            },
            details: {
              description:
                "Specify a success message to display below the toggle element."
            }
          },
          {
            name: "validation",
            type: {
              type: "String",
              additional: "Default: null"
            },
            details: {
              description:
                "Specify the validation rules for the toggle element (check <a href='https://baianat.github.io/vee-validate/guide/rules.html' target='_blank'>VeeValidate documentation</a>)."
            }
          },
          {
            name: "value",
            type: {
              type: "Boolean",
              additional: "Default: false"
            },
            details: {
              description: "Sets the checked state of the toggle element."
            }
          },
          {
            name: "warning",
            type: {
              type: "String",
              additional: "Default: null"
            },
            details: {
              description:
                "Specify a warning message to display below the toggle element."
            }
          }
        ]
      },
      events: {
        fields: [
          {
            name: "name",
            title: "Event Name",
            dataClass: "u-bold",
            width: "150px"
          },
          {
            name: "parameters",
            title: "Parameters",
            width: "150px"
          },
          {
            name: "details",
            title: "Details"
          }
        ],
        data: [
          {
            name: "change",
            parameters: "checked, name, event",
            details: {
              description:
                "Fires the moment when the value of the element is changed"
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

<style lang="scss"></style>
