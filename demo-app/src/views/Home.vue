<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <span>Message: {{ message }}</span>

    <!-- Raw HTML -->
    <p>Using mustaches: {{ rawHtml }}</p>
    <p>Using v-html directive: <span v-html="rawHtml"></span></p>

    <!-- Attribute binding -->
    <!-- <div v-bind:id="dynamicId">test</div> -->

    <!-- Javascript Expressions -->
    <div>{{ number + 1 }}</div>

    <div>{{ number == 101 ? "YES" : "NO" }}</div>

    <div>{{ message.split("").reverse().join("") }}</div>

    <div v-bind:id="'list-' + number"></div>

    <!-- Reactivity -->
    <div>
      <button class="secondary" v-on:click="incrementCount">
        Increment Count
      </button>
    </div>
    <div class="my-2">Count value: {{ count }}</div>
    
    <!-- Class bindings -->
    <div v-bind:class="{ active: isActive }"></div>
    <div
      class="static"
      v-bind:class="{ active: isActive, 'text-danger': hasError }"
    ></div>
    <div v-bind:class="classObject"></div>
    <!-- Array class binding -->
    <div v-bind:class="[activeClass, errorClass]"></div>

    <!-- Conditional Rendering -->
    <div v-if="type === 'A'">A</div>
    <div v-else-if="type === 'B'">B</div>
    <div v-else-if="type === 'C'">C</div>
    <div v-else>Not A/B/C</div>

    <!-- v-if block -->
    <template v-if="ok">
      <h1>Title</h1>
      <p>Paragraph 1</p>
      <p>Paragraph 2</p>
    </template>
    <!-- v-show -->
    <h1 v-show="ok">Hello!</h1>
    <h2 v-show="type == 'A'">A using v-show</h2>
    <!-- List Rendering -->
    <ul id="example-2">
      <li v-for="(item, index) in items" :key="index">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
      </li>
    </ul>
    <!-- List rendering using object-->
    <ul id="v-for-object" class="demo">
      <li v-for="(value, name, index) in object" :key="index">
        {{ index }}. {{ name }}: {{ value }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      type: "D",
      message: "Hello World!!!",
      rawHtml: '<span style="color: red">This should be red.</span>',
      dynamicId: "testId",
      number: 100,
      count: 1,
      // class bindigs
      isActive: true,
      hasError: false,
      classObject: {
        active: true,
        "text-danger": false,
      },
      activeClass: "active",
      errorClass: "text-danger",
      ok: true,
      // items for list rendering
      items: [{ message: "Foo" }, { message: "Bar" }],
      // object for list rendering
      object: {
        title: "How to do lists in Vue",
        author: "Jane Doe",
        publishedAt: "2016-04-10",
      },
    };
  },
  beforeCreate() {
    console.log("Before Created... message in data..", this.message);
    console.log("props..", this.$props);
  },
  created() {
    console.log("created... this.$el .. ", this.$el);
    console.log("$props..", this.$props);
    console.log("In Created... message in data..", this.message);
  },
  beforeMount() {
    console.log("BeforeMounted... this.$el .. ", this.$el);
    console.log("In BeforeMount... message in data..", this.message);
  },
  mounted() {
    console.log("in Mounted...");
    console.log("message property in data...", this.message);
    console.log("this.$el", this.$el);
  },
  beforeUpdate() {
    alert("beforeUpdate: "+this.count);
  },
  updated() {
    console.log("in updated...", this.count)
    alert('one of the data propertyupdated'+this.count);
  },
  methods: {
    incrementCount() {
      this.count += 1;
    },
  },
};
</script>
<style scoped>
</style>
