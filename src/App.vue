<template>
  <div class="App">
    <!-- <router-link to="/about">About</router-link> -->
		<router-view/>
		<Nav />
	</div>
</template>

<script>
import Nav from './components/Nav/Nav2'

export default {
  name: 'App',
  components: {Nav},
	mounted () {
		if (localStorage.getItem("auth") == undefined)
			this.$socket.emit("register");
		else
			this.$socket.emit("auth", { password: localStorage.getItem("password") })

		document.addEventListener('deviceready', onDeviceReady, false);

		function onDeviceReady() {
				alert()
				document.addEventListener('backbutton', function (e) {
						e.preventDefault();
						console.log('Back button prevented page from going back');
						alert('back')
						// Put axios code here
				}, false);
		}
	}
}
</script>


<style lang="scss">
@import '/assets/styles/main.scss';

html {
	width: 100%;
	height: 100%;
	margin: 0;
	padding: 0;
}

body {
	width: 100%;
	margin: 0;
	padding: 0;
	background: url("https://i.pinimg.com/originals/83/4d/59/834d59420f8381b83e62ef1aeede3da7.jpg");
  overflow:hidden;
}

@media screen and (min-width: 600px) {
	body {
		background: url(https://images.hdqwalls.com/download/dragon-winter-snow-anime-manga-4k-9k-1920x1080.jpg);
		background-size: cover;
	}
}

@media screen and (max-width: 600px) {
	body {
		background: url("https://i.pinimg.com/originals/83/4d/59/834d59420f8381b83e62ef1aeede3da7.jpg");
		background-size: auto;
	}
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
	width: 100%;
}

.App {
	width: 100%;
}

#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
