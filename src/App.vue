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

@import "fonts.css";

#page div {
  font-family: "Raleway";
  font-weight: normal;
  max-width: 35em;
  margin: auto;
  font-size: 1rem;
  line-height: 1.25;
  letter-spacing: 0;
  word-spacing: 0;

  font-kerning: normal;
}

#page table {
  font-feature-settings: "lnum" on;
}
@supports (font-variant-numeric: lining-nums) {
  #page table {
    font-feature-settings: normal;
    font-variant-numeric: lining-nums;
  }
}

#page p {
  hyphens: auto;

  margin-bottom: 0;
}
#page p + p {
  margin-top: 0;
}

#page p:first-of-type::first-letter {
  initial-letter: 3;
}

#page .game-term {
  font-variant: small-caps;
}

#page .aspect {
  font-style: italic;
  font-weight: 700;
}

#page .callout {
  font-weight: 300;
  font-size: 0.8rem;
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
  line-height: 1;
}

#page h1 {
  font-size: 3.815rem;
}
#page h2 {
  font-size: 3.052rem;
}
#page h3 {
  font-size: 2.441rem;
}
#page h4 {
  font-size: 1.953rem;
}
#page h5 {
  font-size: 1.563rem;
}
#page h6 {
  font-size: 1.25rem;
}
#page small {
  font-size: 0.8rem;
}

/* @media screen and (min-width: 15em) {
  #page h1 {
    font-size: 3.338rem;
  }
  #page h2 {
    font-size: 2.67rem;
  }
  #page h3 {
    font-size: 2.136rem;
  }
  #page h4 {
    font-size: 1.709rem;
  }
  #page h5 {
    font-size: 1.367rem;
  }
  #page h6 {
    font-size: 1.094rem;
  }
  #page p {
    font-size: 0.875rem;
  }
  #page small {
    font-size: 0.7rem;
  }
} */

@media screen and (min-width: 60em) {
  #page h1 {
    font-size: 4.292rem;
  }
  #page h2 {
    font-size: 3.433rem;
  }
  #page h3 {
    font-size: 2.747rem;
  }
  #page h4 {
    font-size: 2.197rem;
  }
  #page h5 {
    font-size: 1.758rem;
  }
  #page h6 {
    font-size: 1.406rem;
  }
  #page p {
    font-size: 1.125rem;
  }
  #page small {
    font-size: 0.9rem;
  }
}
@media screen and (min-width: 120em) {
  #page h1 {
    font-size: 5.625rem;
  }
  #page h2 {
    font-size: 4.1875rem;
  }
  #page h3 {
    font-size: 3.1875rem;
  }
  #page h4 {
    font-size: 2.375rem;
  }
  #page h5 {
    font-size: 1.75rem;
  }
  #page h6 {
    font-size: 1.3125rem;
  }
  #page p {
    font-size: 1.3125rem;
  }
  #page p {
    font-size: 1.25rem;
  }
  #page small {
    font-size: 0.9rem;
  }
}
</style>
