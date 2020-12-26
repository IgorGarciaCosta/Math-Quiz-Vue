<template>
  <div>
    <button @click="$emit('changeTheme','+')">
      Soma <br /><img src="../icons/clapperboard.png" width="25" height="25" />
    </button>
    <button @click="$emit('changeTheme','-')">
      Subtração <br /><img src="../icons/clapperboard.png" width="25" height="25" />
    </button>
    <button @click="$emit('changeTheme','*')">
      Multiplicação <br /><img src="../icons/clapperboard.png" width="25" height="25" />
    </button>
    <button @click="$emit('changeTheme','/')">
      DIvisão<br />
      <img src="../icons/clapperboard.png" width="25" height="25" />
    </button>
  </div>
</template>

<script>
export default {};
</script>

<style>
</style>