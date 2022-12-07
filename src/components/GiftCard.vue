<template>
  <section class="gift-card__section">
    <div class="container">
        <div class="row">

            <div class="gift-card__desc">
                <h2 class="gift-card-title" v-html="title">
                </h2>
                <p class="gift-card-subtitle" v-html="subtitle"></p>

                <div class="gift-card__links">
                    <a :href="link.url" class="gift-card-link" v-for="(link, idx) in links" :key="idx">
                        {{ link.name }}

                        <i class="fas fa-chevron-right"></i>
                    </a>
                </div>
            </div>

            <img :src="image" alt="" class="gift-card__img">

        </div>
    </div>
  </section>
</template>

<script>
export default {
    name: 'Gift Card',
    data() {
        return {
            title: 'Get <span class="purple-title">supercharged</span> for college',
            subtitle: 'Save on Mac or iPad <span>Plus get a gift card up to $150</span>',
            links: [
                {
                    name: 'Shop Now',
                    url: ''
                }
            ],
            image: require('@/assets/img/giftCard.png')
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

.gift-card__section {
    width: 100%;
    background: #F5F5F7;
    padding-top: 60px;

    .container {
        padding: 0 !important;
    }

    .row {
        flex-direction: column;
        align-items: center;
        text-align: center;

        .gift-card__desc {
            display: flex;
            flex-direction: column;
            align-items: center;

            .gift-card-title {
                color: #000;
                font-size: calc(32px + 4 * (100vw / 1920));
                font-weight: 700;
                max-width: 345px;
                width: 100%;
                font-style: italic;
            }

            .gift-card-subtitle {
                font-size: calc(19px + 1 * (100vw / 1920));
                color: #000;
                font-weight: 500;
                display: flex;
                flex-direction: column;
                text-align: center;
                align-items: center;
            }

            .gift-card__links {
                display: flex;
                align-items: center;
                column-gap: 45px;
                margin-top: 5px;

                .gift-card-link {
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

        .gift-card__img {
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
    .gift-card-title {
        font-size: 36px !important;
    }

    .gift-card-subtitle {
        font-size: 20px !important;
    }

    .gift-card-link {
        font-size: 20px !important;
    }
}



@media (max-width: 662px) {
    .gift-card-title {
        font-size: calc(32px + (4 + 4 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .gift-card-subtitle {
        font-size: calc(19px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .gift-card__links {
        column-gap: 25px !important;
    }

    .gift-card-link {
        font-size: calc(17px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }
}

</style>