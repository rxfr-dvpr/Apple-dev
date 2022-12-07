<template>
  <Swiper :pagination="{clickable: true}" :modules="modules" class="apple__slider" :spaceBetween="15" 
  :slidesPerView="1.5" :centeredSlides="true" :speed="1300" :allowTouchMove="false" >
    <swiper-slide v-for="(slide, idx) in slides" :key="idx" class="apple__slide">
        <div class="slider__desc">
            <a href="" class="stream-now">Stream now <i class="fas fa-play-circle"></i></a>

            <p class="movie-info">
                <span class="movie-genre">{{ slide.genre }}</span>
                &#x2022;
                {{ slide.filmInfo }}
            </p>
        </div>
        <img :src="require(`@/assets/${slide.banner}`)" alt="" class="slider-img">
    </swiper-slide>
  </Swiper>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import 'swiper/scss';
import 'swiper/scss/pagination';
import { Pagination, Autoplay } from 'swiper';

export default {
    name: 'Apple Tv Slider',
    components: {
        Swiper,
        SwiperSlide
    },
    data() {
        return {
            modules: [Pagination, Autoplay],
            slides: [
                {
                    banner: 'img/slider/gutsy.png',
                    genre: 'documentary',
                    filmInfo: 'Women share their strength'
                },
                {
                    banner: 'img/slider/see.png',
                    genre: 'drama',
                    filmInfo: 'The epic series comes to an end' 
                },
                {
                    banner: 'img/slider/fivedays.png',
                    genre: 'drama',
                    filmInfo: 'Based on actual events from Hurricane Katrina' 
                },
                {
                    banner: 'img/slider/blackbird.png',
                    genre: 'drama',
                    filmInfo: "One man's freedom hides in another man's darkness" 
                },
                {
                    banner: 'img/slider/tedlasso.png',
                    genre: 'comedy',
                    filmInfo: "20 Emmy Nomiations including Best Comedy" 
                },
                {
                    banner: 'img/slider/severance.png',     
                    genre: 'triller',
                    filmInfo: "14 Emmy Nominations including Best Drama" 
                },
                {
                    banner: 'img/slider/badsisters.png',     
                    genre: 'drama',
                    filmInfo: "Family. It's a killer" 
                },
                {
                    banner: 'img/slider/life.png',     
                    genre: 'drama',
                    filmInfo: "Write your own story" 
                }
            ]
        }
    }
}
</script>

<style lang="scss" scoped>

.apple__slider {
    max-width: 2535px;
    width: 100%;
    height: 100%;

    .apple__slide {
        width: 100%;
        height: 100%;
        max-height: 550px;
        min-height: 550px;
        opacity: .25;
        transition: .7s;
        transition-delay: .3s;
        position: relative;
        cursor: pointer;

        .slider-img {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: right;
            z-index: -1;
            pointer-events: none;
        }

        .slider__desc {
            width: 100%;
            display: flex;
            column-gap: 45px;
            align-items: center;
            padding: 0 65px;
            position: absolute;
            transition: .8s;
            transition-delay: .7s;
            bottom: 5%;
            opacity: 0;
            transform: translateY(20px);

            .stream-now {
                background: #fff;
                padding: 15px;
                border-radius: 100px;
                display: flex;
                align-items: center;
                column-gap: 7px;
                font-size: 14px;
                color: #000;
                font-weight: 600;
                transition: .4s;

                i {
                    margin-top: 3px;
                    font-size: 15px;
                }

                &:hover {
                    opacity: .8;
                }
            }

            .movie-info {
                display: flex;
                align-items: center;
                font-size: 17px;
                color: #fff;
                gap: 4px;
                pointer-events: none;

                .movie-genre {
                    text-transform: capitalize;
                    font-weight: 600;
                }
            }
        }
    }
}

</style>