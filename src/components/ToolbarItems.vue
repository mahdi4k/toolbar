<template>
  <div class="toolbar">
    <div v-for="item in items" :key="item.shortKey" class="item">
      <input @change='$emit("customChange", $event.target.value)' :ref="item.name" :checked="item.shortKey ==='1'" type="radio" :id="item.shortKey" name="item"
             :value="item.name">

      <label :for="item.shortKey">
      <span>
           <i :class="`icon-${item.icon}`"></i>
      </span>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ToolbarItems',
  data() {
    return {
      items: [
        {name: 'Select', icon: 'hand', shortKey: '1'},
        {name: 'Window', icon: 'window', shortKey: '2'},
        {name: 'Pencil', icon: 'pencil', shortKey: '3'},
        {name: 'MagicPen', icon: 'magicPen', shortKey: '4'},
        {name: 'Brush', icon: 'brush', shortKey: '5'},
        {name: 'Eraser', icon: 'eraser', shortKey: '6'},
        {name: 'Location', icon: 'location', shortKey: '7'},
        {name: 'Crosshairs', icon: 'crosshairs', shortKey: '8'},
      ]
    }
  },
  created() {
    window.addEventListener("keydown", event => {

      if (this.$refs.Select.length) {
        switch (event.key) {
          case 'Escape' :
            this.$refs.Select[0].checked = true
            this.$emit("shortkeySelected", 'Select')
            break;

          case 'a' :
            this.$refs.Window[0].checked = true
            this.$emit("shortkeySelected", 'Window')

            break;

          case 's' :
            this.$refs.Pencil[0].checked = true
            this.$emit("shortkeySelected", 'Pencil')
            break;

          case 'd' :
            this.$refs.MagicPen[0].checked = true
            this.$emit("shortkeySelected", 'MagicPen')
            break;

          case 'f' :
            this.$refs.Brush[0].checked = true
            this.$emit("shortkeySelected", 'Brush')
            break;

          case 'e' :
            this.$refs.Eraser[0].checked = true
            this.$emit("shortkeySelected", 'Eraser')
            break;

          case 'w' :
            this.$refs.Location[0].checked = true
            this.$emit("shortkeySelected", 'Location')
            break;

          case 'q' :
            this.$refs.Crosshairs[0].checked = true
            this.$emit("shortkeySelected", 'Crosshairs')
            break;
        }
      }
    });
  }
}
</script>
<style lang="scss">
.toolbar {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  width: 75px;
  background-color: #4B5162;

  .item {
    &:first-child {
      span {
        padding: 40px 21px;
        border-bottom: 1px solid #363636;
      }
    }

    &:nth-child(2) {
      margin-top: 35px;
    }

    span {
      display: flex;
      cursor: pointer;
      transition: all .2s;
      padding: 11px 20px 11px 20px;
      align-items: center;
      justify-content: center;
      width: 32px;
      height: 32px;

      &:hover {
        background-color: #515666;
      }
    }

  }

  div {
    display: inline-block;
  }

  input[type="radio"] {
    display: none;

    + label {
      color: #333;
      font-family: Arial, sans-serif;
      font-size: 19pt;


    }

    &:checked + label span i {
      color: #2FC570;
    }
  }
}

</style>
