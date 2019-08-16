<template>
  <q-page padding>
    <div class="row q-gutter-xs">
      <div class="col">
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Iure enim harum quibusdam iste nesciunt? Voluptas odit qui doloribus accusantium illo quaerat at recusandae cum, dolor doloremque! Quod quibusdam incidunt itaque.
        <div>
          <q-btn color="teal" label="Show Loading" @click="showLoading ()" />
          <q-btn color="amber" glossy label="Amber" @click="handleClick" />
          <q-btn to="/backend" color="purple" glossy label="backend" />
          <q-btn to="/#" color="primary" label="Logout"/>
          <q-input outlined v-model="myInput" label="Outlined" />
        </div>
        <p
          v-for="n in 50"
          :key="n"
        >Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugit nihil praesentium molestias a adipisci, dolore vitae odit, quidem consequatur optio voluptates asperiores pariatur eos numquam rerum delectus commodi perferendis voluptate?</p>

        <!-- place QPageScroller at end of page -->
        <q-page-scroller position="bottom-right" :scroll-offset="150" :offset="[18, 18]">
          <q-btn fab icon="keyboard_arrow_up" color="accent" />
        </q-page-scroller>
      </div>
      <div
        class="col"
      >Lorem ipsum dolor sit amet consectetur adipisicing elit. Nesciunt veniam culpa quidem qui doloribus asperiores? Rerum eos ducimus minus voluptatibus impedit explicabo dolor repudiandae ex, aliquam illo ea porro laudantium!</div>
    </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      myInput: ''
    }
  },
  methods: {
    handleClick () {
      this.myInput = 'clicked'
    },
    showLoading () {
      this.$q.loading.show({
        message: 'Some important <b>process</b> is in progress.<br/><span class="text-primary">Hang on...</span>'
      })
      // hiding in 3s
      this.timer = setTimeout(() => {
        this.$q.loading.hide()
        this.timer = void 0
      }, 3000)
    }
  }
}
</script>
