<template>
    <nav>
        <img alt="logo" class="logo" src="https://www.123bcc.com/home/img/logo.png" />
        <div class="nav-link-container">
            <a class="nav-link" href="#/login">Đăng nhập</a>
            |
            <a class="nav-link" href="#/reg">Đăng Ký</a>
        </div>
    </nav>
</template>
  
<style scoped>
/* Nav */
nav {
    height: 52px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    /* font-size: 1.07rem; */
    font-size: 17.1px;
    background-image: linear-gradient(83deg,
            rgb(56, 128, 229),
            rgb(117, 155, 255));
    flex-shrink: 0;
    position: sticky;
    top: 0;
    z-index: 100;
}

nav .logo {
    height: 2.73rem;
}

nav .nav-link-container {
    padding-right: 0.5em;
    line-height: 1.2rem;
    font-size: 1.09rem;
}

nav .nav-link {
    display: inline-block;
    padding: 0 0.3em;
    color: inherit;
}

/* End Nav */
</style>
  