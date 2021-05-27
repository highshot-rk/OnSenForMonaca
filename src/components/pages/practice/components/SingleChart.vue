<template>
  <div
    class="total-space"
  >
    <div
        v-bind:style="chartStyle"
        @click="showPopover($event, 'up', false, marks)"
    ></div>
    <p style="font-size: 0.6rem">{{ data }}</p>
    <v-ons-popover cancelable
      :visible.sync="popoverVisible"
      :target="popoverTarget"
      :direction="popoverDirection"
      :cover-target="coverTarget"
    >
      <p style="margin: 0.5rem 1rem;">{{ message }}</p>
      <p style="margin: 0.5rem 1rem"><span class="mark-group">{{ group }}</span> {{ mark }}</p>
    </v-ons-popover>
  </div>
</template>

<script>
export default {
    name: "single-chart",
    data: function() {
        return {
            popoverVisible: false,
            popoverTarget: null,
            popoverDirection: 'up',
            coverTarget: false,
            message: "スイムラブスコア",
            group: "A",
            mark: 78,
        }
    },
    props: [
        "color1",
        "color2",
        "marks",
        "max_marks",
        "data",
    ],
    computed: {
        chartStyle() {
            return {
                "margin-top": (this.max_marks - this.marks) / this.max_marks * 9 + "rem",
                "height": this.marks / this.max_marks * 9 + "rem",
                "background": `linear-gradient(${this.color1},${this.color2})`
            }
        }
    },
    methods: {
        showPopover(event, direction, coverTarget = false, marks) {
            this.popoverTarget = event;
            this.popoverDirection = direction;
            this.coverTarget = coverTarget;
            this.popoverVisible = true;
            this.group = "A";
            this.mark = marks;
        }
    }
}
</script>

<style scoped>
    div.total-space {
        width: 3vw;
        height: 9rem;
    }
    div.total-space div {
        width: 100%;
        border-radius: 100px;
    }
    .mark-group {
        font-size: 3rem;
    }
    p {
        color: #707070;
    }
    div.popover .popover__content  {
      background-color: #ffffffdd;
    }
</style>
