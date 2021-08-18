<template>
  <div class="hello">
    <label> JSON Matriz Input: </label>
    <input type="text" @change="parseMatrix($event)" />
    <button v-on:click="reverseMatrix()">Rotar</button>

    <div class="Container"></div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data: () => {
    return {
      matrix: [],
      reversedMatrix: [],
    };
  },
  methods: {
    reverseMatrix: function () {
      let newArray = new Array(this.matrix.length)
        .fill([])
        .map(() => Array(this.matrix.length).fill([]));
      for (let i = 0; i < this.matrix.length; i++) {
        for (let j = 0; j < this.matrix[i].length; j++) {
          newArray[i][j] = this.matrix[j][i];
        }
      }
      this.reversedMatrix = newArray.reverse();
    },
    parseMatrix: function (e) {
      this.matrix = JSON.parse(e.target.value);
      console.log(this.matrix);
    },
  },
  render: function (createElement) {
    return createElement("h1", "abc");
  },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.Container {
  margin-top: 1rem;
  height: 450px;
  max-height: 450px;
  max-width: 450px;
}

.inline {
  display: flex;
}

.child {
  width: 45px;
  height: 45px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid black;
}
</style>
