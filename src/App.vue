<template>
  <div class="wrapper">
    <header>
      <h1><span>MOO</span>vies</h1>
    </header>
    <main>
      <router-view/>
    </main>

    <nav>
      <ul>
        <li>
          <router-link to="/">Home</router-link>
        </li>
        <li>
          <router-link to="/">Watched</router-link>
        </li>
        <li>
          <router-link to="/">Me</router-link>
        </li>
      </ul>
    </nav>
  </div>
</template>

<style lang="scss">
* {
  box-sizing: border-box;
  border: none;

  &::selection {
    background: transparentize(#42b883, 0.5);
  }
}

body {
  background: white;
}

a,a:link,a:visited,a:hover,a:active{
  text-decoration: none;
  color:inherit;
}

.wrapper {
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  align-content: center;

}

header {
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 50px 16px;
  background-color: white;
  font-size: 75px;
  font-weight: 900;
  border-radius: 0 0 30px 30px;
  box-shadow:  11px 11px 18px #e0e0e0,
  -11px -11px 18px #ffffff;
  margin-bottom: 40px;

  span {
    color: #ffc12b;
  }
}

main {
  flex: 1;
  width: 100vw;
  background-color: white;
  animation: gradient-move 15s ease alternate infinite;

  @keyframes gradient-move {
    0% {
      background-position: 0% 0%;
    }
    100% {
      background-position: 100% 100%;
    }
  }
}

nav {
  width: 100vw;
  ul {
    height: 80px;
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    display: flex;
    align-items: center;
    justify-content: space-around;
    background: rgba(255,255,255, 0.14);
    backdrop-filter: blur(15px);
    border-radius: 30px;

    li {
      //background-color: #ffc12b;
      line-height: 50px;
    }
  }
}
</style>
