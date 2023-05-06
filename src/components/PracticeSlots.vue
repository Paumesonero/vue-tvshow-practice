
<template>
  <div class="header">
    <slot name="header"> </slot>
  </div>
  <div class="body">
    <h1>Body here</h1>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat temporibus
      facilis fuga, adipisci consectetur voluptatem laudantium ratione officiis
      odit ullam quasi, nobis, sed magni sapiente mollitia laboriosam doloremque
      placeat provident!
    </p>
    <slot> </slot>
  </div>
  <div class="footer">
    <slot name="footer"></slot>
  </div>
</template>