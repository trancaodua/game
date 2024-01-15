
<template>
    <div class="mini-box-container">
        <div class="title">
            <div class="sub-left-title">
                <span>ABOUT US</span>
            </div>
        </div>
        <ul class="about-menu">
            <li>
                <img
                    src="data:image/png;base64,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" />
                <span>CSKH</span>
            </li>
            <li>
                <img
                    src="data:image/png;base64,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" />
                <span>APP</span>
            </li>
            <li>
                <img
                    src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADUAAAAwCAMAAACG9cLxAAABX1BMVEUAAAD/YmL/l5f/bW3/k5P/fHz/nJz/j4//lZX/bW3/dHT/ior/V1f/VVX/n5//mZn/kZH/eXn/VFT/dXX/cnL/QED/ZWX/c3P/lJT/c3P/nJz/XFz/f3//lpb/amr/mJj/PT3/nZ3/gID/Wlr/UVH/PDz/kJD/amr/aWn/U1P/lJT/TU3/lpb/Vlb/np7/Pj7/nZ3/lZX/Vlb/aGj/np7/lpb/fHz/m5v/c3P/Z2f/jY3/WFj/kpL/V1f/c3P/YWH/QED/Pj7/YmL/WFj/mJj/cnL/U1P/m5v/iYn/RET/eHj/gID/g4P/hob/Skr/e3v/jIz/X1//jo7/UFD/dXX/TEz/R0f/QUH/Pz//kZH/VFT/c3P/UlL/PDz/fX3/YmL/kJD/k5P/Tk7/XFz/ZGT/Wlr/Zmb/Vlb/cXH/aGj/WFj/fn7/a2v/b2//bW3/mZn/lZX/m5v/l5f/np7/mprRWwJzAAAASHRSTlMAEP4gvyAgEP4w3yD+79/fv4Ag7+/fz7+fn5BvYF9AMCDv7+/v79/f39/Pz6+vn59/f39Q7+/uz8/Pv7++n5CQkJCPf29gX0CTLMCPAAAChklEQVRIx52Sh1caQRDG9wSkGECagIBYYtfY0nsPkSZBohijHCkkwYQD/f9fZga4m4WDh/52Z3b2+/h4cO+ExPi059JzZ7xXvEviIJJzzUtkm4vbc6R5koNS3mazedUEvPo3f3jQRPEKNLt5KNFoNFpQSIRy9ukGai0y3pqnNsZa3aVp3kRyfOcejC1tTGuNQUXMU1ZVc2iaqsJWHQ444arilVTHmuDYdzYmrVbr5FpZxaWWsdTuDBsbik/pY9YE/sGJpUqlUi5DwaaRegUbLtgAmR2WJoSIfLo2j4X94AaIidRB6tpAipFNZbOSjTemgAuFqSyRoc7moQhb5gZQKp3OpOmWbkMCgAKH7u1UOl3njn6dj8fnJZmNwlY/o4UN0Fs9LoSvjpwheqcStrw5LnzX7g8whW0fyUPRQQN2nwB8upknEyAFU5zD7mCjFzuwb4oQ4UMzooLwmZrw653BL724HkYtglCehwN9dgBNSzT4y8D1zqkICWVmz8U+EAxDiLD81XEKE5yGb2HyP50Z01Tbu4Di8oXOsqU/ZFk2fK7/NlhR+kIrzObGT8aj3qcxxV3ufOdMKXJIMrl1LvGCW69lj1sFg/NCIcatGElkIHKKIz39Pdnj1jcJJ7f8ssetH5wFIbEgmdz5Q9xqtyckKW+e+WlYB9mweapWq53UumxiZtddq7l3FRg3ycSGnadOOG6/iLnb4+p74V/F4bRr8tQpUixCI27jrTPSQDauIk8Vh1GlRoecqlarpRJsaDDRAjqnMYLPU6VSLpcrITkccONcIuiSoyWnciPDU59Hhqc+jgxPhQz5aGhonadeHo3IFk8poeORCM0KzuzW4tehHEMtvuqE/gP1XEhdqiNAmgAAAABJRU5ErkJggg==" />
                <span>Ưu đãi</span>
            </li>
            <li>
                <img src="https://www.123bcc.com/home/static-game/img/daily.e1e15b43.svg" />
                <span>Đại lý</span>
            </li>
        </ul>
    </div>
    <div class="description">
        <h4>123B</h4>
        <p> 123B có hơn 10 năm kinh nghiệm hoạt động, là một trong những công ty game an toàn, chất lượng cao và uy tín hàng
            đầu tại Việt Nam, có hàng trăm nghìn hội viên đăng ký. Với tiêu chí khách hàng là trên hết, chúng tôi cung cấp
            trò chơi chất lượng trãi nghiệm tốt nhất và tỷ lệ cược cao như xổ số, thể thao, sòng bạc trực tiếp, xe tăng nổ,
            bắn súng, bắn cá, chọi gà ... và Hỗ trợ đầy đủ các trò chơi trên thiết bị PC, H5, APP, để bạn chơi mọi lúc, mọi
            nơi mà không bị giới hạn. Cung cấp nhiều kênh phương thức thanh toán, gửi và rút tiền nhanh chóng 24/7 luôn đảm
            bảo an toàn giao dịch hội viên. Chúng tôi cam kết mang lại lợi nhuận cực hấp dẫn cho khách hàng thông qua các
            dịch vụ mới và trải nghiệm tốt nhất, chắc chắn là sự lựa chọn ưu tiên nhất để người chơi quay lại với khách hàng
            cũ và mới với nhiều hoạt động ưu đãi chưa từng có trong ngành! 123B uy tín tạo nên thương hiệu là sự lựa chọn
            hàng đầu của bạn. </p>
    </div>
</template>

<style scoped>
.title {
    margin-top: 0.6em;
    margin-bottom: 0.6em;
    padding: 0 1em;
    color: #5c5c5c;
    font-weight: 500;
    font-size: 1.2em;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
}

.sub-left-title {
    display: flex;
    align-items: center;
}

.title-icon-cp {
    background-position: -0.07em -0.07em;
    margin-right: 0.55em;
    margin-left: 0.3em;
    width: 1.3em;
    height: 1.3em;
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites_lobby.323f0720.png);
    background-position: 0 -0.08em;
    background-size: auto 1.45em;
    display: block;
}

.sub-right-title {
    font-size: 0.75em;
    font-weight: 400;
    padding-right: 1.2em;
    padding-top: 0.5em;
    position: relative;
}

.sub-right-title::after {
    content: "";
    display: block;
    width: 0.9em;
    height: 0.9em;
    background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAFKADAAQAAAABAAAAFAAAAACy3fD9AAAC+0lEQVQ4Ec1UTUhUURQ+974ZZ0T8eTNgVLugRYsWRSItEqKiMMJwpqRUoh8YVHR0RFtJLgIj0BEXGkVlQeqoM1IQ0cKgTS2CIhSKCgpSIah55ljjz/Pezpnxvp7T1LoDb8553znnu987994B+N+NKYGnehc3LYvlVwBsIhbyNCicvK8n/kQCuHMd+pF7TWzBnsuMuQXkijVkzwcp6yvD8XYLx4DIEN+bNI2hTil/99iL1mMrORwo+MqA1wBjkgno8nXHy1W95uTViH9D0qPTPUaXwrN5i5CS4yH9PmPQIQFVMDlcFU7sIHyssegjZ8yP4zAFyHZ/OF5NeDazZmhP4swiUsqTSP7e5dZKh+qLDMr7wvE6KWQ/Ni05NEdZpLnwhb2P4g0KVdKbp5/FT3wpJWxfSq5FToxKjXLRFs8AY+wazdQU5kRN+Mdm1aN8VsLrAfYzxyWPA4MvWHhIzMS7VQMu1oSLPcXFtibl0kRjn3SpHPmshJQYafB+5hpUMmAr2Bz0hY1zhONiq648hx9JPyFeOmcaNwhX9ldCKhgPep8BZ3WpYiEHfH3GLopTJ4JDBc54EWddi7O1zu0/CalZOmESXQJ3PgdMWUoYGd+iv0WFb1IvAvalPOEqyOZP98/rsCIeYS4fd3YS53eT6lAVEzPGbQxL8JlzumUb4WSp3UuHG39p2PPLyYeI7sGdnXI7PYcHG1iSqqaLgleQlEaRcAI/GAl63hFOllUhKZg1jUH8zDKc06zb4S5Xd3j9LF7ERVY1TfNFWvXXaar0b1aF04XBq/hdASRbwCtzYKS54AOV44E/hu4OPhw4vxBt0WOE2+0PhbRjqLCNFDBNqxwLeaaooar3ewkqHsGcxhi/FGvRB+1EKt5w9fw9RgU2xOguo4Qz4636XSr0hee3SbH2HMNibLgVbfWeVwSZ3lJYO5AoFiCGiAwY71BkqQYhRtNk7PHO3Z5AJon93aFeTC7xjwRm8GY8iIb0ywonj3d3Fl2cu3V/535m2nOZ8S9QDB5yYzxDrwAAAABJRU5ErkJggg==);
    background-size: cover;
    position: absolute;
    right: 0.2em;
    top: 0.5em;
}

.title-icon-mini {
    background-image: url(https://www.123bcc.com/home/static-game/img/mini_sprites.21b0e003.png);
    margin-right: 0.55em;
    margin-left: 0.3em;
    width: 1.3em;
    height: 1.3em;
    background-size: auto 2.05501rem;
    background-position: -4.38402rem -0.274rem;
}

.title-icon-sp {
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites_lobby.323f0720.png);
    margin-right: 0.55em;
    margin-left: 0.3em;
    width: 1.3em;
    height: 1.3em;
    background-position: -10.2em -0.07em;
    background-size: auto 1.45em;
}

.title-icon-live {
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites_lobby.323f0720.png);
    margin-right: 0.55em;
    margin-left: 0.3em;
    width: 1.3em;
    height: 1.3em;
    background-position: -8.76em -0.07em;
    background-size: auto 1.45em;
}

.about-menu {
    width: 100%;
    height: 5.06em;
    display: flex;
    justify-content: space-between;
    padding: 0 15px;
    align-items: center;
}

.about-menu li {
    background-color: #f2f2f2;
    margin: 0 0.2em;
    text-align: center;
    border-radius: 0.2em;
    padding-top: 0.3em;
    height: 100%;
    box-sizing: border-box;
    flex-grow: 1;
    flex-shrink: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.about-menu img {
    width: auto;
    height: 1.7em;
}

.about-menu span {
    line-height: 2.5em;
    font-size: 0.9em;
    color: rgb(92, 92, 92);
}

.description {
    padding: 2.3em 1.05em 4em 1.05em;
    color: #b9b9b9;
    font-size: 1.25em;
}

.description h4 {
    color: #3a81e5;
    margin-bottom: 0.8em;
}

.description p {
    font-size: .75em;
}
</style>
