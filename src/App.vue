<template>
  <div class="container">
    <router-view />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');

#app {
  font-family: Inter, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--typography-dark, rgba(0, 0, 0, 0.95));
  background: #FFF;
  margin-left: auto;
  margin-right: auto;

  --typography-dark: #000000F2;
  --typography-medium: #000000B2;
  --typography-light: #0000008C;
  --ui-error: #C71B1B;
  --ui-grey: #DDE1E3;
  --ui-lightblue: #CFEBFF;
  --ui-lightgrey: #F3F3F3;
  --ui-yellow: #FFC163;
}

h1 {
  font-size: 56px;
  font-family: Inter;
  font-weight: 700;
}

h2 {
  font-size: 48px;
  font-family: Inter;
  font-weight: 700;
}

h3 {
  font-size: 32px;
  font-family: Inter;
  font-weight: 700;
}

.container {
  display: flex;
  padding: 72px 0px 35px 0px;
  justify-content: center;
  align-items: center;
}

.link {
  font-size: 16px;
  font-family: Inter;
  font-weight: 700;
  line-height: 24px;
  text-decoration-line: underline;
}

.title {
  font-size: 24px;
  font-family: Inter;
  font-weight: 700;
}

.body-large-bold {
  font-size: 18px;
  font-family: Inter;
  font-weight: 700;
  line-height: 28px;
}

.body-bold {
  font-size: 16px;
  font-family: Inter;
  font-weight: 700;
  line-height: 24px;
}

.caption-bold {
  font-size: 14px;
  font-family: Inter;
  font-weight: 700;
}

.extra-small-bold {
  font-size: 12px;
  font-family: Inter;
  font-weight: 700;
}

.body-l-regular {
  font-size: 18px;
  font-family: Inter;
  line-height: 28px;
}

.body-regular {
  font-size: 16px;
  font-family: Inter;
  line-height: 24px;
}

.caption-regular {
  font-size: 14px;
  font-family: Inter;
}

.extra-small-regular {
  font-size: 12px;
  font-family: Inter;
}</style>
