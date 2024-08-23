<template>

    <footer>
        <div class="footer-links">
            <h3><a>Contact Us</a></h3>
            <div class="social-media">
                <a><img class="social" src="../assets/images/facebook.png" alt=""></a>
                <a><img class="social" src="../assets/images/instagram.png" alt=""></a>
                <a><img class="social" src="../assets/images/twitter.png" alt=""></a>
            </div>
            <h3>&copy; Movie News, 2023</h3>
        </div>
        <img class="megaphone" src="../assets/images/megaphone.png" alt="">
    </footer>
    
</template>

<style scoped>
    footer{
        background-color: #8C0343;
        display: flex;
        padding: 0.8em 1.5em;
        align-items: center;
        position: -webkit-sticky;
        position: sticky;
        bottom: 0;
        max-height: 100px;
    }

    .social-media{
        display: flex;
        max-width: 20px;
    }

    .social{
        max-width: 20px;
    }

    .footer-links{
        flex: 1;
    }

    .megaphone{
        max-width: 110px;
        max-height: 110px;
        flex: 1;
    }  
    
    h3{
        margin: 0.2em;
    }
    
    
</style>

