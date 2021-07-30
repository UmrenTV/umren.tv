<template>
  <div class="footer" id="footer">
    <h1 class="title">Footer</h1>
    <div class="credits">
      <p class="credits-text">
        The source of this project can be found at the
        <a href="https://github.com/UmrenTV/umren.tv" target="_blank"
          >Github repository.</a
        >
      </p>
    </div>
  </div>
</template>


<style lang="scss">
.footer {
  padding: 0.4vh 4vw;
  height: 60vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  border-top: 1px dotted rgba(0, 0, 0, 0.7);
}
.credits {
  margin-top: auto;
}
.credits-text a {
  font-weight: 500;
  text-decoration: none;
  color: var(--color-primary);
  transition: 0.2s ease-in-out;
}
.credits-text:hover a {
  color: black;
}
</style>
