<template>
  <div class="block">
    Click me
  </div>
</template>

<script>
export default {
    props: ['delay']
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        padding: 100px 0;
        text-align: center;
        margin: 40px auto;
        transition: background-color 0.5s;
    }
</style>