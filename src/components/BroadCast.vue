
<template>
    <div class="broadcast-container">
        <div class="animated">
            <p>
                【Nhắc nhở an toàn】:1. Nếu nhận được cuộc gọi thông báo 123b đã
                sát nhập vào một công ty nào đó và yêu cầu khách hàng chuyển tiền
                vào số tài khoản công ty đó thì vui lòng không bị mắc bẫy kẻ gian,
                công ty 123B khuyến cáo không chuyển tiền, cung cấp thông tin cá
                nhân, tài khoản ngân hàng, mật khẩu,... cho bất kì ai dưới mọi
                hình thức 。 2. Kẻ gian lợi dụng lúc hệ thống bảo trì định kì của
                công ty , thông qua các phương tiện truyền thông tuyên truyền công
                ty đã đổi tên miền mới và cần chuyển tiền vào tài khoản công ty
                khác... vui lòng đừng tin thông tin đó, công ty chúng tôi không
                thông báo trên bất kì phương tiện truyền thông。 3. Hiện nay trên
                thị trường rất nhiều trò lừa đảo dùng danh nghĩa 123B để lừa đảo,
                vui lòng cẩn thận và ghi nhớ trang wep chính thức của công ty
                chúng tôi là 123b.net để tránh bị lừa. Nếu khách hàng bị lừa từ
                các wep có tên miền không thuộc quyền sở hữu của công ty 123B -
                chúng tôi sẽ không chịu bất kỳ trách nhiệm.
            </p>
        </div>
    </div>
</template>

<style scoped>
.broadcast-container {
    display: flex;
    flex-wrap: wrap;
    padding-left: 2.8em;
    height: 2.35em;
    background-color: #edf3ff;
    white-space: nowrap;
    font-size: 0.9rem;
    line-height: 2.25em;
    position: relative;
}

.broadcast-container::before {
    background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAIKADAAQAAAABAAAAIAAAAACshmLzAAACHUlEQVRYCe1WPUgcQRT+5u4QNOGwCBYK6kEKi5BOErSxMooEIYWN8ey0UKzUQFJ4tWfhDxKw9LzmIKBIkiatjbYpJAE9IQSbgCSgELh9fhNwzB03uzvrX+E9WHbevJ/vmzdvZheoyX2vgLpqAUay0iSCHPM8Z7K3uVm16pIz5uJc6UvwJ55glwR6+SQ9IFPpE6RHJpBekH6C7kDQZkAEj8w45CASgddZmSx52NarDoljdUtYLVUMhYLEt4pYEg8TVcyRpkITGF6W5NYhCkR5EQnJElRGgE2V4upWoNDD8j4oizkr065NMQQyBan7XsQnZu5gY11Z0ll56nl41dCI+bVxdWpLaJrwsIhOAnfYHF3nS4IxrmPu9MS/XwwBnuFmVxA//7jCpraLwkRGxOBUxlgNlY6u+vqM+sKb8Ye+J4qLaLXF3xiBf4AK3/Tb+4vUnRBgD3BnKTHE74QAy/9YAycSOLh1AqPz0k3QdqVw3NeCo0ACbIafNqco8yUgreO4De+HhhTV6mKaMNWOPd6A+9Xd3GcJ/IGr30g+5M3qIzwpl+J7FV+6+Y7ybwjrIKGd9ccIZ8EfI1cCZguCSOen1O/BFAa4TU6/XEF5QxPQiXQz5WfVJElM8bE2VhDo/3YnAheBJLESj+Eld/vPxVzUdyQCGmx9Wn0mgS5Wwpxx6ieuRCIT0EC5GfW1vg7P2Mkf+fziT8w7VwI1/1oFzgGyZIxkf7AJUAAAAABJRU5ErkJggg==);
    position: absolute;
    top: 0.6em;
    left: 1em;
    width: 1.2em;
    height: 1.2em;
    background-size: 100%;
    content: "";
}

.animated {
    overflow: hidden;
    width: 100%;
    white-space: nowrap;
}

.animated>* {
    display: inline-block;
    position: relative;
    left: 100%;
    animation: grow 150s linear infinite;
    color: #a8acb3;
}

@keyframes grow {
    0% {
        transform: translateX(0%);
    }

    100% {
        transform: translateX(-100%);
    }
}
</style>
