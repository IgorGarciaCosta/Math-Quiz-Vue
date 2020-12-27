<template>
  <div>
    <button @click="$emit('changeTheme','+')">
      Soma <br /><img src="../icons/add.png" width="20" height="20" />
    </button>
    <button @click="$emit('changeTheme','-')">
      Subtração <br /><img src="../icons/minus-symbol.png" width="20" height="20" />
    </button>
    <button @click="$emit('changeTheme','*')">
      Multiplicação <br /><img src="../icons/multiplication-sign.png" width="20" height="20" />
    </button>
    <button @click="$emit('changeTheme','/')">
      Divisão<br />
      <img src="../icons/division.png" width="20" height="20" />
    </button>
  </div>
</template>

<script>
export default {};
</script>

<style>
  button{
    color: black;
    font-weight: 500;
  }
</style>