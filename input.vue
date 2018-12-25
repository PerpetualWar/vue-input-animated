<template>
  <div>
    <input
      :type="type"
      :value="value"
      @input="$emit('input', $event.target.value)"
      :class="{ active: value !== '' }"
    />
    <span class="input-name">{{ placeholder }}</span>
  </div>
</template>

<script>
export default {
  name: 'Input',
  props: {
    autoSelect: { type: Boolean, default: false },
    type: { type: String, default: 'text' },
    value: { type: String },
    placeholder: { type: String },
  },
  mounted() {
    console.log(this);
    if (this.autoSelect) {
      this.$el.children[0].select();
    }
  },
};
</script>

<style lang="scss" scoped>
@import '../../../assets/sass/variables.scss';

.input {
  display: block;
  position: relative;
  margin-bottom: 3em;
  min-height: 50px;
  height: 50px;
}

input {
  display: block;
  font-family: $font;
  font-weight: 400;
  font-size: 1rem;
  width: 100%;
  border: 0;
  border-bottom: 1px solid #cccccc;
  padding-bottom: 5px;
  transition: 0.25s;

  &:focus,
  &:active {
    outline: 0;
    border-color: $color-btngrey;
  }
}

input.active + .input-name {
  transform: translateY(-59px);
  // transform: translateY(-79px);
  font-size: 0.9em;
  color: $color-dkgrey;
}

.input-name {
  font-size: 0.9rem;
  // font-size: 1rem;
  font-family: $font;
  font-weight: 400;
  color: #cccccc;
  transform: translateY(-27px);
  // transform: translateY(-53px);
  position: absolute;
  transition: 0.25s;

  &:hover {
    cursor: text;
  }
}
</style>
