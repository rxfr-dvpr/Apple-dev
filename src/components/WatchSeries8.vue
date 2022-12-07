<template>
  <section class="watch-8__section">
    <div class="container">
        <div class="row">

            <div class="watch-8__desc">
                <h2 class="watch-8-title" v-html="title">
                </h2>
                <p class="watch-8-subtitle">{{ subtitle }}</p>

                <div class="watch-8__links">
                    <a :href="link.url" class="watch-8-link" v-for="(link, idx) in links" :key="idx">
                        {{ link.name }}

                        <i class="fas fa-chevron-right"></i>
                    </a>
                </div>
            </div>

            <img :src="image" alt="" class="watch-8__img">

        </div>
    </div>
  </section>
</template>

<script>

export default {
    name: 'Watch Series 8',
    data() {
        return {
            title: '<i class="fab fa-apple"></i> WATCH <span class="red-subtitle">SERIES 8</span>',
            subtitle: 'A healthy leap ahead',
            links: [
                {
                    name: 'Learn more',
                    url: ''
                },
                {
                    name: 'Order now',
                    url: ''
                }
            ],
            image: require('@/assets/img/watchSeries8.png')
        }
    }
}

</script>

<style lang="scss" scoped>

@keyframes translateRight {
    from {
        transform: translateX(0);
    }
    to {
        transform: translateX(3px);
    }
}

.watch-8__section {
    width: 100%;
    background: #000;
    padding-top: 60px;

    .container {
        padding: 0 !important;
    }

    .row {
        flex-direction: column;
        align-items: center;
        text-align: center;

        .watch-8__desc {
            display: flex;
            flex-direction: column;
            align-items: center;

            .watch-8-title {
                color: #fff;
                font-size: calc(32px + 4 * (100vw / 1920));
                font-weight: 700;
            }

            .watch-8-subtitle {
                font-size: calc(19px + 1 * (100vw / 1920));
                color: #fff;
                font-weight: 500;
            }

            .watch-8__links {
                display: flex;
                align-items: center;
                column-gap: 45px;
                margin-top: 5px;

                .watch-8-link {
                    font-size: calc(17px + 1 * (100vw / 1920));
                    color: #2997ff;
                    display: flex;
                    align-items: center;
                    column-gap: 10px;
                    font-weight: 500;

                    & > i {
                        font-size: 14px;
                        margin-top: 4px;
                        transition: .4s;
                    }

                    &:hover {
                        
                        & > i {
                            animation: translateRight .6s linear infinite;
                        }
                    }
                }
            }
        }

        .watch-8__img {
            max-width: 450px;
            width: 100%;
            cursor: none;
            pointer-events: none;
            object-fit: cover;
        }
    }
}


@media (max-width: 1024px) {
    .watch-8__img {
        padding: 0 15px;
    }
}

@media (min-width: 1920px) {
    .watch-8-title {
        font-size: 36px !important;
    }

    .watch-8-subtitle {
        font-size: 20px !important;
    }

    .watch-8-link {
        font-size: 20px !important;
    }
}



@media (max-width: 662px) {
    .watch-8-title {
        font-size: calc(32px + (4 + 4 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .watch-8-subtitle {
        font-size: calc(19px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .watch-8__links {
        column-gap: 25px !important;
    }

    .watch-8-link {
        font-size: calc(17px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }
}

</style>