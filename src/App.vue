<template>
    <div id="app" class="page-container">
        <md-app md-waterfall md-mode="fixed">
            <md-app-toolbar class="md-primary">
                <md-button class="md-icon-button" @click="showNavigation = true">
                    <md-icon>menu</md-icon>
                </md-button>
                <span class="md-title">BookShelf
                    <md-icon>keyboard_arrow_right</md-icon>{{book.title}}</span>
            </md-app-toolbar>
            <md-app-drawer :md-active.sync="showNavigation">
                <md-toolbar class="md-primary" md-elevation="0">
                    <img src="./assets/logo.png" alt="BookShelf">
                </md-toolbar>
                <md-list>
                    <md-list-item @click="pushNav('./')">
                        <h2>{{book.title}}</h2>
                    </md-list-item>
                    <md-list-item md-expand v-for="section in book.sections" :key="section.name">
                        <span class="md-list-item-text">{{section.name}}</span>
                        <md-list slot="md-expand">
                            <md-list-item class="md-inset" v-for="nestedPage in section.pages" :key="nestedPage.path" @click="pushNav(nestedPage.path)">
                                <span class="md-list-item-text">{{nestedPage.name}}</span>
                            </md-list-item>
                        </md-list>
                    </md-list-item>
                    <md-list-item v-for="page in book.pages" :key="page.path" @click="pushNav(page.path)">
                        <span class="md-list-item-text">{{page.name}}</span>
                    </md-list-item>
                </md-list>
            </md-app-drawer>
            <md-app-content>
                <div id="page">
                    <router-view></router-view>
                </div>
            </md-app-content>
        </md-app>
    </div>
</template>

<script>
import Book from "@/book";

export default {
  name: "app",
  data() {
    return {
      book: {},
      showNavigation: false
    };
  },
  created() {
    this.book = Book;
  },
  components: {},
  methods: {
    pushNav(path) {
      // note - a little hack to correct pathing issues.
      var p = path.substring(1).replace(/ /g, "-");
      this.showNavigation = false;
      this.$router.push(p);
    }
  }
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css?family=Roboto:300,400,500,700,400italic");
@import url("https://fonts.googleapis.com/icon?family=Material+Icons");

@import "~vue-material/dist/theme/engine";

@include md-register-theme("default", (
   primary: md-get-palette-color(indigo, 900), 
   accent: md-get-palette-color(blue, 200),
   theme: dark
));

@import "~vue-material/dist/theme/all";

.md-app {
  height: 100vh;
}
</style>

<style>
/* You can adjust these styles to layout your pages. */
@import url("https://fonts.googleapis.com/css?family=Abel|Raleway:300,300i,400,400i,700,700i");

#page div {
  font-family: "Raleway";
  font-weight: normal;
  max-width: 35em;
  margin: auto;
  font-size: 1rem;
  line-height: 1.15;
  letter-spacing: 0;
  word-spacing: 0;

  font-feature-settings: "onum" 1;
}

@supports (font-variant-numeric: oldstyle-nums) {
  #page div {
    font-feature-settings: normal;
    font-variant-numeric: oldstyle-nums;
  }
}

#page p {
  hyphens: auto;
  margin-bottom: 0;
}
#page p + p {
  margin-top: 0;
}

#page h1,
#page h2,
#page h3,
#page h4,
#page h5,
#page h6 {
  text-align: left;
  font-family: "Abel";
  font-weight: normal;
}

#page h1 {
  font-size: 2.75rem; /* 44px */
}
#page h2 {
  font-size: 2.375rem; /* 38px */
}
#page h3 {
  font-size: 2.0625rem; /* 33px */
}
#page h4 {
  font-size: 1.5625rem; /* 25px */
}
#page h5 {
  font-size: 1.3125rem; /* 21px */
}
#page h6 {
  font-size: 1rem; /* 16px */
}

@media screen and (min-width: 60em) {
  #page h1 {
    font-size: 4.1875rem; /* 67px */
  }
  #page h2 {
    font-size: 3.1875rem; /* 51px */
  }
  #page h3 {
    font-size: 2.75rem; /* 44px */
  }
  #page h4 {
    font-size: 2.0625rem; /* 33px */
  }
  #page h5 {
    font-size: 1.5625rem; /* 25px */
  }
  #page h6 {
    font-size: 1.125rem; /* 18px */
  }
  #page p {
    font-size: 1.125rem; /* 18px */
  }
}
@media screen and (min-width: 120em) {
  #page h1 {
    font-size: 5.625rem; /* 90px */
  }
  #page h2 {
    font-size: 4.1875rem; /* 67px */
  }
  #page h3 {
    font-size: 3.1875rem; /* 51px */
  }
  #page h4 {
    font-size: 2.375rem; /* 38px */
  }
  #page h5 {
    font-size: 1.75rem; /* 28px */
  }
  #page h6 {
    font-size: 1.3125rem; /* 21px */
  }
  #page p {
    font-size: 1.3125rem; /* 21px */
  }
}
</style>
