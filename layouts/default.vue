<template>
  <!--    <div>-->
  <!--      <nuxt />-->
  <!--    </div>-->
  <div class="ma-12 pa-12">
    <v-app-bar
      color="deep-purple"
      dark
    >
      <v-app-bar-nav-icon @click="drawer = true"/>

      <v-toolbar-title>My vue lab</v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
      src="https://c-ssl.duitang.com/uploads/item/201505/05/20150505191905_VQWvr.jpeg"
    >
      <v-list>
        <v-list-item>
          <v-list-item-avatar style="margin-left:20%;height: 100px; width: 100px;">
            <v-img src="/avatar.png"/>
          </v-list-item-avatar>
        </v-list-item>
        <v-list-item link>
          <v-list-item-content>
            <v-list-item-title>Giria</v-list-item-title>
            <v-list-item-subtitle><a href="https://github.com/giriawsh" style="text-decoration: none; color: #090a0f" target="_blank">giriawsh@github.com</a></v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-divider/>
      <v-list
        rounded
      >
        <!--          <v-subheader>菜单栏</v-subheader>-->
        <v-list-item-group color="primary">
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            link
            @click="$router.push({ path: item.to })"
          >
            <v-list-item-icon style="padding-right: 10px;">
              <v-icon>{{item.icon}}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{item.title}}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <nuxt/>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        drawer: false,
        items: [
          {icon: 'mdi-apps', title: 'Home', to: '/'},
          {icon: 'mdi-alpha-t-circle-outline', title: 'liquidText', to: '/svgDemo/liquidText'},
          {icon: 'mdi-flask-round-bottom', title: 'colorDemo', to: '/colorDemo/colorTab'},
          {icon: 'mdi-music-circle', title: 'musicLab', to: '/colorDemo/colorTab'},
        ],
      }
    },
    methods: {}
  }
</script>
<style>
  html {
    font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
    font-size: 16px;
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
  }

  *,
  *:before,
  *:after {
    box-sizing: border-box;
    margin: 0;
  }

  .button--green {
    display: inline-block;
    border-radius: 4px;
    border: 1px solid #3b8070;
    color: #3b8070;
    text-decoration: none;
    padding: 10px 30px;
  }

  .button--green:hover {
    color: #fff;
    background-color: #3b8070;
  }

  .button--grey {
    display: inline-block;
    border-radius: 4px;
    border: 1px solid #35495e;
    color: #35495e;
    text-decoration: none;
    padding: 10px 30px;
    margin-left: 15px;
  }

  .button--grey:hover {
    color: #fff;
    background-color: #35495e;
  }
</style>
