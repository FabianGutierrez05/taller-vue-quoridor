<script>
export default{
    props: {
        label: String,
        onClick: Function,
    },
};
</script>
<template>
    <button @click="onClick" class="btn">{{ label }} </button>
</template>
<style scoped>
.btn{
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 16px;
  min-width: 150px;
  font-size: 12px;
  height: 30px;
  border-radius: 15px;
  cursor: pointer;
  box-shadow: 0px 0px 1px 1px rgb(0, 0, 0/28%);
}
</style>