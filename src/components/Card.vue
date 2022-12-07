<template>
  <section class="card__section">
    <div class="container">
        <div class="row">

            <div class="card__desc">
                <h2 class="card-title" v-html="title">
                </h2>
                <p class="card-subtitle" v-html="subtitle"></p>

                <div class="card__links">
                    <a :href="link.url" class="card-link" v-for="(link, idx) in links" :key="idx">
                        {{ link.name }}

                        <i class="fas fa-chevron-right"></i>
                    </a>
                </div>
            </div>

            <img :src="image" alt="" class="card__img">

        </div>
    </div>
  </section>
</template>

<script>

export default {
    name: 'Card',
    data() {
        return {
            title: '<i class="fab fa-apple"></i> Card',
            subtitle: 'Get up to 3% Daily Cash back with every purchase',
            links: [
                {
                    name: 'Learn more',
                    url: ''
                },
                {
                    name: 'Apply now',
                    url: ''
                }
            ],
            image: require('@/assets/img/card.png')
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

.card__section {
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

        .card__desc {
            display: flex;
            flex-direction: column;
            align-items: center;
            max-width: 280px;
            width: 100%;

            .card-title {
                color: #000;
                font-size: calc(32px + 4 * (100vw / 1920));
                font-weight: 700;
            }

            .card-subtitle {
                font-size: calc(19px + 1 * (100vw / 1920));
                color: #000;
                font-weight: 500;
                display: flex;
                flex-direction: column;
                text-align: center;
                align-items: center;
            }

            .card__links {
                display: flex;
                align-items: center;
                column-gap: 45px;
                margin-top: 5px;

                .card-link {
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

        .card__img {
            max-width: 330px;
            width: 100%;
            cursor: none;
            pointer-events: none;
            object-fit: cover;
            margin-top: auto;
        }
    }
}

@media (min-width: 1920px) {
    .card-title {
        font-size: 36px !important;
    }

    .card-subtitle {
        font-size: 20px !important;
    }

    .card-link {
        font-size: 20px !important;
    }
}



@media (max-width: 662px) {
    .card__section {
        .row {
            row-gap: 15px;
        }
    }

    .card-title {
        font-size: calc(32px + (4 + 4 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .card-subtitle {
        font-size: calc(19px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .card__links {
        column-gap: 25px !important;
    }

    .card-link {
        font-size: calc(17px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }
}

</style>