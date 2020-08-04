<template>
  <div class="ClassTest">
    <h1>Homepage</h1>
    <p class="red white--text">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Animi, dolorem ducimus eligendi, error excepturi facere facilis magni modi mollitia pariatur perspiciatis, porro praesentium quas repellat sed sit tempore veniam voluptates!</p>
    <p class="pink lighten-3 red--text text--darken-3">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium asperiores autem debitis dolor dolorum ducimus ex, iste laboriosam laudantium libero magni, nisi provident quibusdam. Debitis dignissimos earum laboriosam nam sunt.</p>
    <h1 class="display-4">Massive display</h1>
    <h4 class="display-1">Smaller display</h4>
    <p class="headline font-weight-bold"> this is headline</p>

    <v-btn class="pink white--text lighten-3">click me</v-btn>
    <v-btn dark color="pink ">click me</v-btn>
    <v-btn dark depressed color="pink ">click me</v-btn>
    <v-btn text color="pink">click me</v-btn>
    <v-btn depressed class="pink white--text">
<!--      这里使用了v-icon之后只需要在里面放对应的icon的名字即可转换成图标-->
      <v-icon left>mdi-email</v-icon>
      <span>email me</span>
    </v-btn>


    <v-btn depressed small class="pink white--text">
      <v-icon small left>mdi-email</v-icon>
      <span>email me</span>
    </v-btn>


    <v-btn depressed large class="pink white--text">
      <span>email me</span>
      <v-icon large right>mdi-email</v-icon>
    </v-btn>

    <v-btn depressed small dark color="purple">
      <span>email me</span>
      <v-icon small right>mdi-email</v-icon>
    </v-btn>

<!--    fab会把包围的变园-->
    <v-btn fab depressed small dark color="purple">
      <v-icon small>mdi-thumb-up</v-icon>
    </v-btn>


      <!--    这表示在比md分辨率低的情况下不显示-->
      <v-btn class="hidden-md-and-down">click me</v-btn>
      <!--这种表示比md分辨率高的情况下显示-->
      <v-btn class="hidden-md-and-up blue white--text">click me</v-btn>

      <v-btn class="hidden-sm-only red white--text">click me</v-btn>

  </div>
</template>

<script>


export default {
  name: 'ClassTest',
  components: {
  }
}
</script>
