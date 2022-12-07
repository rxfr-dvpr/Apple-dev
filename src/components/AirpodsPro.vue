<template>
  <section class="airpods-pro__section">
    <div class="container">
        <div class="row">

            <div class="airpods__desc">
                <h2 class="airpods-title">
                    {{ title }}
                </h2>
                <p class="airpods-subtitle">{{ subtitle }}</p>

                <div class="airpods__links">
                    <a :href="link.url" class="airpods-link" v-for="(link, idx) in links" :key="idx">
                        {{ link.name }}

                        <i class="fas fa-chevron-right"></i>
                    </a>
                </div>
            </div>

            <img :src="image" alt="" class="airpods__img">

        </div>
    </div>
  </section>
</template>

<script>

export default {
    name: 'Airpods Pro',
    data() {
        return {
            title: 'Airpods Pro',
            subtitle: 'Rebuilt from the sound up.',
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
            image: require('@/assets/img/airpodsPro.png')
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

.airpods-pro__section {
    width: 100%;
    background: #000;
    padding-top: 60px;

    .row {
        flex-direction: column;
        align-items: center;
        text-align: center;

        .airpods__desc {
            display: flex;
            flex-direction: column;
            align-items: center;

            .airpods-title {
                color: #fff;
                font-size: calc(32px + 24 * (100vw / 1920));
                font-weight: 700;
            }

            .airpods-subtitle {
                font-size: calc(19px + 7 * (100vw / 1920));
                color: #fff;
            }

            .airpods__links {
                display: flex;
                align-items: center;
                column-gap: 45px;
                margin-top: 5px;

                .airpods-link {
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

        .airpods__img {
            max-width: 600px;
            width: 100%;
            cursor: none;
            pointer-events: none;
        }
    }
}

@media (min-width: 1920px) {
    .airpods-title {
        font-size: 56px !important;
    }

    .airpods-subtitle {
        font-size: 26px !important;
    }

    .airpods-link {
        font-size: 20px !important;
    }
}



@media (max-width: 662px) {
    .airpods-title {
        font-size: calc(32px + (24 + 24 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .airpods-subtitle {
        font-size: calc(19px + (7 + 7 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .airpods__links {
        column-gap: 25px !important;
    }

    .airpods-link {
        font-size: calc(17px + (3 + 3 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }
}

</style>