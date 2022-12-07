<template>
  <section class="iphone-14__section">
    <div class="container">
        <div class="row">

            <div class="iphone__desc">
                <h2 class="iphone-title">
                    {{ title }}
                </h2>
                <p class="iphone-subtitle">{{ subtitle }}</p>

                <div class="iphone__links">
                    <a :href="link.url" class="iphone-link" v-for="(link, idx) in links" :key="idx">
                        {{ link.name }}

                        <i class="fas fa-chevron-right"></i>
                    </a>
                </div>
            </div>

            <img :src="image" alt="" class="iphone__img">

        </div>
    </div>
  </section>
</template>

<script>

export default {
    name: 'iPhone 14',
    data() {
        return {
            title: 'iPhone 14',
            subtitle: 'Big and bigger',
            links: [
                {
                    name: 'Learn more',
                    url: ''
                },
                {
                    name: 'Buy',
                    url: ''
                }
            ],
            image: require('@/assets/img/iphone14.png')
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

.iphone-14__section {
    width: 100%;
    background: #f5f5f5;
    padding-top: 60px;

    .row {
        flex-direction: column;
        align-items: center;
        text-align: center;

        .iphone__desc {
            display: flex;
            flex-direction: column;
            align-items: center;

            .iphone-title {
                color: #000;
                font-size: calc(32px + 24 * (100vw / 1920));
                font-weight: 700;
            }

            .iphone-subtitle {
                font-size: calc(19px + 7 * (100vw / 1920));
                color: #000;
                font-weight: 500;
            }

            .iphone__links {
                display: flex;
                align-items: center;
                column-gap: 45px;
                margin-top: 5px;

                .iphone-link {
                    font-size: calc(17px + 3 * (100vw / 1920));
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

        .iphone__img {
            max-width: 500px;
            width: 100%;
            cursor: none;
            pointer-events: none;
            object-fit: cover;
        }
    }
}

@media (min-width: 1920px) {
    .iphone-title {
        font-size: 56px !important;
    }

    .iphone-subtitle {
        font-size: 26px !important;
    }

    .iphone-link {
        font-size: 20px !important;
    }
}



@media (max-width: 662px) {
    .iphone-title {
        font-size: calc(32px + (24 + 24 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .iphone-subtitle {
        font-size: calc(19px + (7 + 7 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .iphone__links {
        column-gap: 25px !important;
    }

    .iphone-link {
        font-size: calc(17px + (3 + 3 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }
}

</style>