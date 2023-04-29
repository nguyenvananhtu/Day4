<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" integrity="sha512-iecdLmaskl7CVkqkXNQ/ZH/XLlvWZOJyj7Yy7tcenmpD1ypASozpmT/E0iPtmFIB46ZmdtAc9eNBvH0H/ZpiBw==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <title>Document</title>
</head>
<style>
    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    body{
        height: 100vh;
        background-color: #4158D0;
        background-image: linear-gradient(43deg, #4158D0 0%, #C850C0 46%, #FFCC70 100%);
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .wrapper{
        width: 1200px;
        display: flex;
        flex-wrap: wrap;
        margin: auto;
        justify-content: space-between;
    }
    img{
        width: 100%;
        height: 100%;
        object-position: center;
        object-fit: cover;
        transition: 0.25s;
        border-radius: 10px;
        border: 10px solid transparent;
        border-image: linear-gradient(to bottom right, #b827fc 0%, #2c90fc 25%, #b8fd33 50%, #fec837 75%, #fd1892 100%);
        border-image-slice: 1;
    }
    .image{
        width: 22%;
        height: 200px;
        border-radius: 10px;
        overflow: hidden;
        margin: 20px 0;
        
    }
    .image:hover img{
        transform: scale(1.3);
    }

    .gallery{
        position: fixed;
        width: 100%;
        height: 100%;
        background: rgb(0, 0, 0, 0.6);
        display: flex;
        align-items: center;
        color: white;
        opacity: 0;
        pointer-events: none;
        transform: scale(0.8);
        transition: 0.5s;
    }
    .close{
        position: fixed;
        top: 15px;
        right: 25px;
        font-size: 35px;
    }
    .control{
        font-size: 35px;
        color: rgba(255, 255, 255, 0.8);
        position: absolute;
    }
    .prev{
        left: 15px;
    }
    .next{
        right: 15px;
    }
    .gallery_inner{
        width: 50%;
        height: 90%;
        margin: 0 auto;
        overflow: hidden;
    }
    
    .show{
        opacity: 1;
        pointer-events: auto;
        transform: scale(1);
    }
    .hide{
        display: none;
    }
</style>
<body>
    <div class="wrapper">
        <div class="image">
            <img src="https://taimienphi.vn/tmp/cf/aut/anh-gai-xinh-1.jpg" alt="">
        </div>
        <!-- image day3 -->
        <div class="image">
            <img src="https://samkyvuong.vn/wp-content/uploads/2022/04/gai-han.jpg" alt="">
        </div>
        <!-- image day3 -->
        <div class="image">
            <img src="https://i.pinimg.com/originals/30/31/1e/30311e920a4939fed09036528bf8c955.jpg" alt="">
        </div>
        <!-- image day3 -->
        <div class="image">
            <img src="https://cdn.vn.alongwalk.info/vn/wp-content/uploads/2023/02/15162247/image-tong-hop-99-anh-gai-xinh-dang-yeu-ca-tinh-nhat-hien-nay-167642776733001.jpg" alt="">
        </div>
        <!-- image day3 -->
        <div class="image">
            <img src="https://kynguyenlamdep.com/wp-content/uploads/2022/06/anh-gai-trung-quoc-cuc-dep.jpg" alt="">
        </div>
        <!-- image day3 -->
        <div class="image">
            <img src="https://hinhnen4k.com/wp-content/uploads/2023/02/anh-gai-xinh-vn-2.jpg" alt="">
        </div>
        <!-- image day3 -->
        <div class="image">
            <img src="https://vothisaucamau.edu.vn/wp-content/uploads/2023/01/03191304-8-anh-gai-xinh-toc-dai.jpeg" alt="">
        </div>
        <!-- image day3 -->
        <div class="image">
            <img src="https://fsc.edu.vn/wp-content/uploads/2023/03/1678897140_737_TOP-200-Anh-Gai-Cute-Sieu-De-Thuong-Dang.jpg" alt="">
        </div>
    </div>


    <div class="gallery">
        <i class="fas fa-times close"></i>
        <div class="gallery_inner">
            <img src="https://fsc.edu.vn/wp-content/uploads/2023/03/1678897140_737_TOP-200-Anh-Gai-Cute-Sieu-De-Thuong-Dang.jpg" alt="">
        </div>
        <div class="control prev">
            <i class="fa-solid fa-chevron-left"></i>
        </div>
        <div class="control next">
            <i class="fa-solid fa-chevron-right"></i>
        </div>
    </div>
    </div>
</body>
<script>
    var images = document.querySelectorAll('.image img')
    var prev = document.querySelector('.prev')
    var next = document.querySelector('.next')
    var close = document.querySelector('.close')
    var galleryImg = document.querySelector('.gallery_inner img')
    var gallery = document.querySelector('.gallery')

    var currentIndex = 0;

    function showGallery() {
        if (currentIndex == 0) {
            prev.classList.add('hide')
        } else {
            prev.classList.remove('hide')
        }

        if (currentIndex == images.length - 1) {
            next.classList.add('hide')
        } else {
            next.classList.remove('hide')
        }

        galleryImg.src = images[currentIndex].src
        gallery.classList.add('show')
    }

    images.forEach((item, index) => {
        item.addEventListener('click', function () {
            currentIndex = index
            showGallery()
        })
    })

    close.addEventListener('click', function () {
        gallery.classList.remove('show')
    })

    document.addEventListener('keydown', function (e) {
        if (e.keyCode == 27) {
            gallery.classList.remove('show')
        }
    })

    next.addEventListener('click', function () {
        if (currentIndex < images.length - 1) {
            currentIndex++
            showGallery()
        }
    })

    prev.addEventListener('click', function () {
        if (currentIndex > 0) {
            currentIndex--
            showGallery()
        }
    })
   
        
</script>
</html>
