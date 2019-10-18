<template>
    <div>
        <header class="header">
            <div>
                <nuxt-link to="/" class="header-item header-logo">
                    TravelWithUs
                </nuxt-link>
            </div>
            <nav class="header-right">
                <ul>
                    <li class="header-item">
                        <nuxt-link to="/unimplemented">
                            LOGIN
                        </nuxt-link>
                    </li>
                    <li class="header-item">
                        <nuxt-link to="/unimplemented">
                            POST
                        </nuxt-link>
                    </li>
                    <li class="header-item">
                        <nuxt-link to="/unimplemented">
                            LANGUAGE
                        </nuxt-link>
                    </li>
                    <li class="header-item">
                        <nuxt-link to="/">
                            HOME
                        </nuxt-link>
                    </li>
                </ul>
            </nav>
        </header>
    </div>
</template>

<style scoped>
/** css reset */

a, nuxt-link {
    text-decoration: none;
    color: white;
}

a:hover, nuxt-link:hover {
    text-decoration: none;
    color: white;
}

/** nav bar css */

.header {
    overflow: hidden;
    background-color: rgb(140, 175, 185);
    font-family: "SF Pro Text","SF Pro Icons","Helvetica Neue","Helvetica","Arial",sans-serif;
    width: 100vw;
    min-width: 270px;
    z-index: 100;
    position: fixed;
}

.header-logo {
    font-weight: bolder;
    background: rgb(239, 50, 47);
}

.header-item {
    float: left;
    color: white;
    text-align: center;
    padding: 0.5vh 1.8vw;
    text-decoration: none;
    font-size: 4vw;
    line-height: 5vh;
}

.header-right {
    float: right;
}
</style>