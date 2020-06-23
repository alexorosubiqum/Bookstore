<template>
  <div>
    <header>
      <div class="logo">
        <h1>UBIQUM'S BOOKSTORE</h1>
      </div>
      <div id="search">
        <input class="search-input" type="text" placeholder="SEARCH BOOKS..." v-model="search" />
      </div>
    </header>
    <main>
      <div id="allBooks">
        <div v-for="(book, i) in filteredBooks" class="everyBook" :key="i">
          <div class="flip">
            <div class="front">
              <img :src="book.cover" />
            </div>
            <div class="back">
              <h3>{{ book.title }}</h3>
              <p>{{ book.description }}</p>
              <button class="buttons" v-bind:href="book.detail" data-fancybox="gallery">MORE INFO</button>
            </div>
          </div>
        </div>
        <div class="noBooksMessage" v-if="filteredBooks.length == 0">
          <h2>NO MATCHES</h2>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      url: "https://api.myjson.com/bins/zyv02",
      books: [],
      search: ""
    };
  },
  created() {
    fetch(this.url)
      .then(data => data.json())
      .then(json => {
        this.books = json.books;
        console.log(this.books);
      });
  },

  computed: {
    filteredBooks() {
      return this.books.filter(book => {
        return book.title.toLowerCase().includes(this.search.toLowerCase());
      });
    }
  }
};
</script>

<style>
/*
body {
  background-repeat: no-repeat;

  margin: auto;
  margin-top: 1.5%;
  text-align: center;
  font-family: "Nova Square";
}

header {
  background-color: lightslategray;
  border-radius: 10px;
  display: flex;
  align-content: center;
  width: 80%;
  margin: auto;
}
.logo {
  margin: auto;
  display: flex;
  margin-left: 5%;
}

#search {
  margin-right: 5%;
}
.search-input {
  background-color: transparent;
  margin-top: 20%;
  border-radius: 5px;
}
::placeholder {
  color: white;
  font-family: "Nova Square";
}



.everyBook {
  perspective: 1000px;
}
.everyBook:hover .flip,
.everyBook.hover .flip {
  transform: rotateY(180deg);
}

.everyBook .front,
.everyBook .back {
  width: 100%;
  height: 340px;
}

.flip {
  transition: transform 0.5s;
  transform-style: preserve-3d;
  position: relative;
}

.front,
.back {
  backface-visibility: hidden;
  position: absolute;
  top: 0;
  left: 0;
}

.front {
  z-index: 2;
  transform: rotateY(0deg);
  border-radius: 10px;
}

.front img {
  height: 100%;
  width: 100%;
  border-radius: 10px;
}

.back {
  transform: rotateY(180deg);
  background-color: rgba(119, 136, 153, 0.1);
  text-align: center;
  display: flex;
  justify-content: center;
  flex-direction: column;
  border-radius: 10px;
}

.buttons {
  color: white;
  border-radius: 5px;
  background-color: lightslategray;
  border-color: transparent;
  text-align: center;
  font-family: "Nova Square";
}

#allBooks {
  display: flex;
  flex-wrap: wrap;
  width: 80%;
  margin: auto;
  margin-top: 10px;
  justify-content: center;
} */

body {
  background-image: url(/images/bgBooks.jpg);
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;
  margin: auto;
  margin-top: 1.5%;
  text-align: center;
  font-family: "Nova Square";
}

body h1,
h3 {
  text-transform: uppercase;
  color: white;
}

body p {
  color: white;
}

main {
  width: 100%;
}
header {
  background-color: lightslategray;
  border-radius: 10px;
  display: flex;
  align-content: center;
  width: 80%;
  margin: auto;
}
.logo {
  margin: auto;
  display: flex;
  margin-left: 5%;
}

#search {
  margin-right: 5%;
}
.search-input {
  background-color: transparent;
  margin-top: 20%;
  border-radius: 5px;
}
::placeholder {
  color: white;
  background-color: rgba(119, 136, 153, 0.3);
  font-family: "Nova Square";
}
/* ---------------------------------------------------------------------------- */

.everyBook {
  perspective: 1000px;
}
.everyBook:hover .flip,
.everyBook.hover .flip {
  transform: rotateY(180deg);
}

.everyBook {
  width: 20%;
  height: 340px;
  margin-bottom: 10px;
}

.everyBook .front,
.everyBook .back {
  width: 100%;
  height: 340px;
}

.flip {
  transition: transform 0.5s;
  transform-style: preserve-3d;
  position: relative;
  margin: 5px;
}

.front,
.back {
  backface-visibility: hidden;
  position: absolute;
  top: 0;
  left: 0;
}

.front {
  z-index: 2;
  transform: rotateY(0deg);
  border-radius: 10px;
}

.front img {
  height: 100%;
  width: 100%;
  border-radius: 10px;
}

.back {
  transform: rotateY(180deg);
  background-color: rgba(119, 136, 153, 0.5);
  text-align: center;
  display: flex;
  justify-content: center;
  flex-direction: column;
  border-radius: 10px;
}

#buttons {
  color: white;
  border-radius: 5px;
  background-color: lightslategray;
  border-color: transparent;
  text-align: center;
  font-family: "Nova Square";
  margin-right: auto;
  margin-left: auto;
}

#allBooks {
  display: flex;
  flex-wrap: wrap;
  width: 80%;
  margin: auto;
  margin-top: 10px;
  justify-content: center;
}

.noBooksMessage {
  /* color: white;
  background-color: lightslategray;
  border-radius: 10%;
  margin: auto;
  width: auto; */
  color: white;
  background-color: lightslategray;
  border-radius: 10px;
  /* display: flex; */
  text-align: center;
  width: auto;
  padding-left: 10px;
  padding-right: 10px;
  margin: auto;
}
</style>
