<template>
  <section class="watch-ultra__section">
    <div class="container">
        <div class="row">

            <div class="watch__desc">
                <h2 class="watch-title" v-html="title">
                </h2>
                <p class="watch-subtitle">{{ subtitle }}</p>

                <div class="watch__links">
                    <a :href="link.url" class="watch-link" v-for="(link, idx) in links" :key="idx">
                        {{ link.name }}

                        <i class="fas fa-chevron-right"></i>
                    </a>
                </div>
            </div>

            <img :src="image" alt="" class="watch__img">

        </div>
    </div>
  </section>
</template>

<script>

export default {
    name: 'Watch Ultra',
    data() {
        return {
            title: '<i class="fab fa-apple"></i> WATCH <span class="orange-subtitle">ULTRA</span>',
            subtitle: 'Adventure awaits',
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
            image: require('@/assets/img/watchUltra.png')
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

.watch-ultra__section {
    width: 100%;
    background: #FBFBFD;
    padding-top: 60px;

    .container {
        padding: 0 !important;
    }

    .row {
        flex-direction: column;
        align-items: center;
        text-align: center;

        .watch__desc {
            display: flex;
            flex-direction: column;
            align-items: center;

            .watch-title {
                color: #000;
                font-size: calc(32px + 4 * (100vw / 1920));
                font-weight: 700;
            }

            .watch-subtitle {
                font-size: calc(19px + 1 * (100vw / 1920));
                color: #000;
                font-weight: 500;
            }

            .watch__links {
                display: flex;
                align-items: center;
                column-gap: 45px;
                margin-top: 5px;

                .watch-link {
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

        .watch__img {
            max-width: 750px;
            width: 100%;
            cursor: none;
            pointer-events: none;
            object-fit: cover;
            margin-top: auto;
        }
    }
}

@media (min-width: 1920px) {
    .watch-title {
        font-size: 36px !important;
    }

    .watch-subtitle {
        font-size: 20px !important;
    }

    .watch-link {
        font-size: 20px !important;
    }
}



@media (max-width: 662px) {
    .watch-title {
        font-size: calc(32px + (4 + 4 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .watch-subtitle {
        font-size: calc(19px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .watch__links {
        column-gap: 25px !important;
    }

    .watch-link {
        font-size: calc(17px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }
}

</style>