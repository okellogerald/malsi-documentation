<template>
    <div class="layout">
        <header class="header">
            <nav class="nav">
                <g-link class="nav__link" to="/architecture/">ARCHITECTURE</g-link>
                <g-link class="nav__link" to="/flow/">FLOW</g-link>
            </nav>
        </header>
        <slot />
    </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style>
body {
    font-family: "Circular";
    margin: 0;
    padding: 0;
    line-height: 1.5;
}

.layout {
    max-width: 760px;
    margin: 0 auto;
    padding-left: 20px;
    padding-right: 20px;
}

.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
    height: 80px;
}

.nav__link {
    margin-left: 20px;
}
</style>

<style>
@font-face {
    font-family: Gopher-Mono;
    src: url('../assets/fonts/GopherMono-Regular.ttf');
    font-weight: normal;
}
@font-face {
    font-family: Circular;
    src: url('../assets/fonts/Circular.otf');
    font-weight: normal;
}
</style>