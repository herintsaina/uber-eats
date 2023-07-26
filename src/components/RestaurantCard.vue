<template>
  <div class="restaurant--card">
    <div class="restaurant--image"></div>  
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss">
    .restaurant--card{
        width: 32%;
        height: 30vh;

        .restaurant--image {
            background-image: url("https://cn-geo1.uber.com/image-proc/resize/eats/format=webp/width=550/height=440/quality=70/srcb64=aHR0cHM6Ly9kMXJhbHNvZ25qbmczNy5jbG91ZGZyb250Lm5ldC8zNzg4MDJiMC1jNTI4LTQ4MjktYjBiNS0wY2M2NDBkZjYzY2QuanBlZw==");
            height: 70%;
            background-size: cover;
            background-position: center;
        }
    }
</style>