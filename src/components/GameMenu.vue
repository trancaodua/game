
<template>
    <div class="game-menu-container">
        <ul class="game-menu">
            <li class="game-menu-item">
                <i class="game-menu-icon nav_icon_cp"></i>
                <span class="game-menu-name">Xổ Số</span>
            </li>
            <li class="game-menu-item">
                <i class="game-menu-icon nav_icon_mini"></i>
                <span class="game-menu-name">Trò Chơi</span>
            </li>
            <li class="game-menu-item">
                <i class="game-menu-icon nav_icon_sp"></i>
                <span class="game-menu-name">Thể Thao</span>
            </li>
            <li class="game-menu-item">
                <i class="game-menu-icon nav_icon_live"></i>
                <span class="game-menu-name">Casino</span>
            </li>
            <li class="game-menu-item">
                <i class="game-menu-icon nav_icon_dz"></i>
                <span class="game-menu-name">Nổ Hũ</span>
            </li>
            <li class="game-menu-item">
                <i class="game-menu-icon nav_icon_by"></i>
                <span class="game-menu-name">Bắn Cá</span>
            </li>
        </ul>
        <div class="menu-pagination-container">
            <div class="menu-pagination"></div>
        </div>
    </div>
</template>

<style scoped>
.game-menu {
    display: flex;
    flex-direction: row;
    padding: 0.57em 0.685rem 0.57em 0.822rem;
    height: 5.275em;
    width: 100%;
    list-style: none;
}

.game-menu-item {
    border: 1px solid #ededed;
    border-radius: 0.274rem;
    margin-right: 0.274rem;
    padding: 0.2055rem 0 0;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 0;
    height: auto;
    flex-grow: 1;
    flex-shrink: 1;
}

.game-menu-icon {
    position: relative;
    display: block;
    background-repeat: no-repeat;
    width: 2.28rem;
    height: 2.28rem;
    background-size: 38.857rem 2.28rem;
    background-position: -11.43rem 0;
}

.nav_icon_cp {
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites.c88b3d69.png);
}

.nav_icon_mini {
    background-size: auto 2.15776rem;
    background-position: 0 0;
    background-image: url(https://www.123bcc.com/home/static-game/img/mini_sprites.21b0e003.png);
}

.nav_icon_sp {
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites.c88b3d69.png);
    background-position: -20.57rem 0;
}

.nav_icon_live {
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites.c88b3d69.png);
    background-position: -9.14rem 0;
}

.nav_icon_dz {
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites.c88b3d69.png);
    background-position: -18.285rem 0;
}

.nav_icon_by {
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites.c88b3d69.png);
    background-position: -6.857rem 0;
}

.game-menu-name {
    font-size: 0.7535rem;
    color: #a4acb5;
    line-height: 1.17;
    width: 100%;
    text-align: center;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    margin-top: 0.137rem;
}

.menu-pagination-container {
    display: flex;
    justify-content: center;
    align-items: center;
}

.menu-pagination {
    background: #edf1f5;
    width: 24px;
    height: 0.214em;
    border-radius: 0.143em;
    /* transition-property: background,color,translate3d,border,box-shadow; */
    position: relative;
}

.menu-pagination::after {
    background: #528ded;
    content: "";
    width: 14px;
    height: 0.214em;
    border-radius: 0.143em;
    display: block;
    transition: all 0.1s ease-in-out;
    -webkit-transform: translateX(0);
    transform: translateX(0);
}

</style>
