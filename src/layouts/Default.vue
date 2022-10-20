<template>
    <div class="layout">
        <header class="header">
            <strong>
                <h1>MALSI</h1>
            </strong>
            <nav class="nav">
                <g-link class="nav__link" to="/">ARCHITECTURE OVERVIEW</g-link>
                <g-link class="nav__link" to="/about/">PAGES IN DETAIL</g-link>
                <g-link class="nav__link" to="/about/">STATE-NOTIFIERS IN DETAIL</g-link>
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
    font-family: "Gopher-Mono";
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
</style>