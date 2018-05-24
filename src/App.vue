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

@include md-register-theme(
  "default",
  (
    primary: md-get-palette-color(indigo, 900),
    accent: md-get-palette-color(blue, 200),
    theme: dark
  )
);

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
  font-synthesis: none;
  font-feature-settings: "salt" on;
}

#page a {
  text-decoration: none;
  color: #90caf9;
}
#page a:hover,
#page a:focus {
  border-bottom: 1px solid #90caf9;
}
@supports (text-decoration-skip: ink) {
  #page a:hover,
  #page a:focus {
    text-decoration-skip: ink;
    -webkit-text-decoration-skip: skip;
    border-bottom: 0;
    border-bottom: 1px solid #90caf9;
  }
}

#page table {
  font-feature-settings: "lnum" on;
  border-collapse: collapse;
  margin: 0;
}

@supports (font-variant-numeric: lining-nums) {
  #page table {
    font-feature-settings: normal;
    font-variant-numeric: lining-nums;
  }
}

#page td,
#page th {
  padding: 0.125em 0.5em 0.25em 0.5em;
  line-height: 1;
}

#page figure {
  max-width: 100%;
  overflow-x: auto;
  margin: 0;
}

#page .quoted {
  display: flex;
  flex-direction: column;
}
#page .quoted p {
  order: 1;
}
#page .quoted p::before {
  content: "«";
  margin-left: -1ch;
}
#page .quoted p::after {
  content: "»";
}
#page .quoted footer {
  order: 2;
}
/* insert a long dash and a narrow non-breaking space before the quote attribution */
#page .quoted footer::before {
  content: "—\202F";
}

#page ul {
  padding-left: 0;
  margin-left: 0;
  list-style: none;
}

#page li {
  hyphens: auto;
  margin-top: 0;
  margin-bottom: 0.25em;
}

#page ul li::before {
  content: "–";
  margin-right: 0.5em;
}

#page ul li {
  text-indent: -1em;
  list-style: none;
}

#page p {
  hyphens: auto;
  margin-top: 0;
  margin-bottom: 0.5em;
}

#page p:first-of-type::first-letter {
  initial-letter: 3;
}

#page .game-term {
  font-variant: small-caps;
}

#page .aspect {
  font-style: italic;
  font-weight: bold;
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
  margin-top: 0.5em;
  margin-bottom: 0.5em;
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
/* Aside styles */
#page aside,
#page article {
  margin-left: 1em;
  margin-right: 1em;
  margin-top: 0;
  margin-bottom: 0;
  font-weight: 300;
  font-size: 0.8rem;
  line-height: 1.5625;
}
#page aside p,
#page article p {
  font-size: 0.8rem;
}
#page aside h1,
#page article h1 {
  font-size: 3.052rem;
}
#page aside h2,
#page article h2 {
  font-size: 2.441rem;
}
#page aside h3,
#page article h3 {
  font-size: 1.953rem;
}
#page aside h4,
#page article h4 {
  font-size: 1.563rem;
}
#page aside h5,
#page article h5 {
  font-size: 1.25rem;
}
#page aside h6,
#page article h6 {
  font-size: 1rem;
}

@media screen and (min-width: 49em) {
  /* breakpoint for text intrusion sidebars */
  #page aside.left {
    width: 11.5em;
    float: left;
    margin-left: -5.75em;
  }
  #page aside.right {
    width: 11.5em;
    float: right;
    margin-right: -5.75em;
  }
  #page article.left {
    width: 30em;
    float: left;
    margin-left: -15em;
  }
  #page article.right {
    width: 30em;
    float: right;
    margin-right: -15em;
  }
}
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
  #page aside,
  #page article {
    font-size: 0.9rem;
  }
  #page aside.left {
    width: 11.5em;
    float: left;
    margin-left: -12.5em;
  }
  #page aside.right {
    width: 11.5em;
    float: right;
    margin-right: -12.5em;
  }
  #page aside p,
  #page article p {
    font-size: 0.9rem;
  }
  #page aside h1,
  #page article h1 {
    font-size: 3.433rem;
  }
  #page aside h2,
  #page article h2 {
    font-size: 2.747rem;
  }
  #page aside h3,
  #page article h3 {
    font-size: 2.197rem;
  }
  #page aside h4,
  #page article h4 {
    font-size: 1.758rem;
  }
  #page aside h5,
  #page article h5 {
    font-size: 1.406rem;
  }
  #page aside h6,
  #page article h6 {
    font-size: 1.125rem;
  }
}
@media screen and (min-width: 90em) {
  #page aside.left {
    width: 20em;
    float: left;
    margin-left: -21em;
  }
  #page aside.right {
    width: 20em;
    float: right;
    margin-right: -21em;
  }
  #page article.left {
    width: 38em;
    float: left;
    margin-left: -23em;
  }
  #page article.right {
    width: 38em;
    float: right;
    margin-right: -23em;
  }
}
@media screen and (min-width: 120em) {
  #page h1 {
    font-size: 5.009rem;
  }
  #page h2 {
    font-size: 4.007rem;
  }
  #page h3 {
    font-size: 3.206rem;
  }
  #page h4 {
    font-size: 2.564rem;
  }
  #page h5 {
    font-size: 2.052rem;
  }
  #page h6 {
    font-size: 1.641rem;
  }
  #page p {
    font-size: 1.3125rem;
  }
  #page small {
    font-size: 1.05rem;
  }
  #page aside,
  #page article {
    font-size: 1.05rem;
  }
  #page aside.left {
    width: 25em;
    float: left;
    margin-left: -26em;
  }
  #page aside.right {
    width: 25em;
    float: right;
    margin-right: -26em;
  }
  #page article.left {
    width: 38em;
    float: left;
    margin-left: -23em;
  }
  #page article.right {
    width: 38em;
    float: right;
    margin-right: -23em;
  }
  #page aside p,
  #page article p {
    font-size: 1.05rem;
  }
  #page aside h1,
  #page article h1 {
    font-size: 4.007rem;
  }
  #page aside h2,
  #page article h2 {
    font-size: 3.206rem;
  }
  #page aside h3,
  #page article h3 {
    font-size: 2.564rem;
  }
  #page aside h4,
  #page article h4 {
    font-size: 2.052rem;
  }
  #page aside h5,
  #page article h5 {
    font-size: 1.641rem;
  }
  #page aside h6,
  #page article h6 {
    font-size: 1.313rem;
  }
}
</style>
