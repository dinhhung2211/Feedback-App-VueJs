<template>
  <div>
    <ul class="rating">
      <li>
        <input
          v-model="ratingSelect"
          type="radio"
          id="num1"
          name="rating"
          value="1"
          @change="changeRating"
        />
        <label for="num1">1</label>
      </li>
      <li>
        <input
          v-model="ratingSelect"
          type="radio"
          id="num2"
          name="rating"
          value="2"
          @change="changeRating"
        />
        <label for="num2">2</label>
      </li>
      <li>
        <input
          v-model="ratingSelect"
          type="radio"
          id="num3"
          name="rating"
          value="3"
          @change="changeRating"
        />
        <label for="num3">3</label>
      </li>
      <li>
        <input
          v-model="ratingSelect"
          type="radio"
          id="num4"
          name="rating"
          value="4"
          @change="changeRating"
        />
        <label for="num4">4</label>
      </li>
      <li>
        <input
          v-model="ratingSelect"
          type="radio"
          id="num5"
          name="rating"
          value="5"
          @change="changeRating"
        />
        <label for="num5">5</label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["rating"],
  data() {
    return {
      ratingSelect: this.rating,
    };
  },
  methods: {
    changeRating() {
      this.$emit("ratingChanged", this.ratingSelect);
    },
  },
  watch: {
    rating(newValue) {
      this.ratingSelect = newValue; // Update when the prop changes
    },
  },
};
</script>

<style>
.rating {
  display: flex;
  align-items: center;
  justify-content: space-around;
  margin: 30px 0 40px;
  list-style: none;
}

.rating li,
.num-display {
  position: relative;
  background: #f4f4f4;
  width: 50px;
  height: 50px;
  padding: 10px;
  text-align: center;
  border-radius: 50%;
  font-size: 19px;
  border: 1px #eee solid;
  transition: 0.3s;
}

.rating li label {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 50px;
  height: 50px;
  padding: 10px;
  border-radius: 50%;
  transform: translate(-50%, -50%);
  cursor: pointer;
}

.rating li:hover,
.num-display {
  background: #ff6a95;
  color: #fff;
}

[type="radio"] {
  opacity: 0;
}

[type="radio"]:checked ~ label {
  background: #ff6a95;
  color: #fff;
}
</style>
