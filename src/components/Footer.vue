<template>
  <footer class="footer">
    <div class="container">
        <div class="row">
            
            <div class="footer__column-list">

                <div class="footer__column" v-for="(column, idx) in footerColumnLinks" :key="idx">
                    <ul class="footer__list" v-for="(item, id) in column.linksList" :key="id">
                        <p class="footer__list-title">{{ item.subtitle }}</p>
                        <li class="footer__list-item" v-for="(link, idd) in item.links" :key="idd">
                            <a :href="link.url" class="footer__list-link">{{ link.name }}</a>
                        </li>
                    </ul>
                </div>

            </div>

            <div class="footer__copyrights">
                <p class="footer__copyright-shop" v-html="footerCopyrights.copyrightShop"></p>

                <span class="line"></span>

                <div class="footer__copyright-legal">
                    <p class="legal-info">{{ footerCopyrights.copyrightLegal.info }}</p>

                    <ul class="legal__list">
                        <li class="legal__list-item" v-for="(list, idx) in footerCopyrights.copyrightLegal.list" :key="idx">
                            <a :href="list.url" class="legal__list-link">{{ list.name }}</a>
                        </li>
                    </ul>

                    <a :href="localeLink.url" class="locale-link" target="_blank">{{ localeLink.name }}</a>
                </div>
            </div>

        </div>
    </div>
  </footer>
</template>

<script>

export default {
    name: 'Footer',
    data() {
        return {
            footerColumnLinks: [
                {
                    linksList: [
                        {
                            subtitle: 'Shop and Learn',
                            links: [
                                {
                                    name: 'Store',
                                    url: ''
                                },
                                {
                                    name: 'Mac',
                                    url: ''
                                },
                                {
                                    name: 'iPad',
                                    url: ''
                                },
                                {
                                    name: 'iPhone',
                                    url: ''
                                },
                                {
                                    name: 'Watch',
                                    url: ''
                                },
                                {
                                    name: 'AirPods',
                                    url: ''
                                },
                                {
                                    name: 'TV & Home',
                                    url: ''
                                },
                                {
                                    name: 'AirTag',
                                    url: ''
                                },
                                {
                                    name: 'Accessories',
                                    url: ''
                                },
                                {
                                    name: 'Gift Cards',
                                    url: ''
                                }
                            ]
                        }
                    ]
                },
                {
                    linksList: [
                        {
                            subtitle: 'Services',
                            links: [
                                {
                                    name: 'Apple Music',
                                    url: ''
                                },
                                {
                                    name: 'Apple TV+',
                                    url: ''
                                },
                                {
                                    name: 'Apple Fitness+',
                                    url: ''
                                },
                                {
                                    name: 'Apple News+',
                                    url: ''
                                },
                                {
                                    name: 'Apple Arcade',
                                    url: ''
                                },
                                {
                                    name: 'iCloud',
                                    url: ''
                                },
                                {
                                    name: 'Apple One',
                                    url: ''
                                },
                                {
                                    name: 'Apple Card',
                                    url: ''
                                },
                                {
                                    name: 'Apple Books',
                                    url: ''
                                },
                                {
                                    name: 'Apple Podcasts',
                                    url: ''
                                },
                                {
                                    name: 'App Store',
                                    url: ''
                                }
                            ]
                        },          
                        {
                            subtitle: 'Account',
                            links: [
                                {
                                    name: 'Manage Your Apple ID',
                                    url: ''
                                },
                                {
                                    name: 'Apple Store Account',
                                    url: ''
                                },
                                {
                                    name: 'iCloud.com',
                                    url: ''
                                }
                            ]
                        },
                    ]
                },
                {
                    linksList: [
                        {
                            subtitle: 'Apple Store',
                            links: [
                                {
                                    name: 'Find a Store',
                                    url: ''
                                },
                                {
                                    name: 'Genius Bar',
                                    url: ''
                                },
                                {
                                    name: 'Today at Apple',
                                    url: ''
                                },
                                {
                                    name: 'Apple Camp',
                                    url: ''
                                },
                                {
                                    name: 'Apple Store App',
                                    url: ''
                                },
                                {
                                    name: 'Refurbished and Clearance',
                                    url: ''
                                },
                                {
                                    name: 'Financing',
                                    url: ''
                                },
                                {
                                    name: 'Apple Trade In',
                                    url: ''
                                },
                                {
                                    name: 'Order Status',
                                    url: ''
                                },
                                {
                                    name: 'Shopping Help',
                                    url: ''
                                }
                            ]
                        }
                    ]
                },
                {
                    linksList: [
                        {
                            subtitle: 'For Business',
                            links: [
                                {
                                    name: 'Apple and Business',
                                    url: ''
                                },
                                {
                                    name: 'Shop for Business',
                                    url: ''
                                }
                            ]
                        },
                        {
                            subtitle: 'For Education',
                            links: [
                                {
                                    name: 'Apple and Education',
                                    url: ''
                                },
                                {
                                    name: 'Shop for K-12',
                                    url: ''
                                },
                                {
                                    name: 'Shop for College',
                                    url: ''
                                }
                            ]
                        },
                        {
                            subtitle: 'For Healthcare',
                            links: [
                                {
                                    name: 'Apple in Healthcare',
                                    url: ''
                                },
                                {
                                    name: 'Health on Apple Watch',
                                    url: ''
                                },
                                {
                                    name: 'Health Records on iPhone',
                                    url: ''
                                }
                            ]
                        },
                        {
                            subtitle: 'For Government',
                            links: [
                                {
                                    name: 'Shop for Government',
                                    url: ''
                                },
                                {
                                    name: 'Shop for Veterans and Military',
                                    url: ''
                                },
                            ]
                        }
                    ]
                },
                {
                    linksList: [
                        {
                            subtitle: 'For Business',
                            links: [
                                {
                                    name: 'Accessibility',
                                    url: ''
                                },
                                {
                                    name: 'Education',
                                    url: ''
                                },
                                {
                                    name: 'Environment',
                                    url: ''
                                },
                                {
                                    name: 'Inclusion and Diversity',
                                    url: ''
                                },
                                {
                                    name: 'Privacy',
                                    url: ''
                                },
                                {
                                    name: 'Racial Equity and Justice',
                                    url: ''
                                },
                                {
                                    name: 'Supplier Responsibility',
                                    url: ''
                                },
                            ]
                        },
                        {
                            subtitle: 'About Apple',
                            links: [
                                {
                                    name: 'Newsroom',
                                    url: ''
                                },
                                {
                                    name: 'Apple Leadership',
                                    url: ''
                                },
                                {
                                    name: 'Career Opportunities',
                                    url: ''
                                },
                                {
                                    name: 'Investors',
                                    url: ''
                                },
                                {
                                    name: 'Ethics & Compliance',
                                    url: ''
                                },
                                {
                                    name: 'Events',
                                    url: ''
                                },
                                {
                                    name: 'Contact Apple',
                                    url: ''
                                },
                            ]
                        }
                    ]
                }
            ],
            footerDropdownLinks: [
                {
                    subtitle: 'Shop and Learn',
                    links: [
                        {
                            name: 'Store',
                            url: ''
                        },
                        {
                            name: 'Mac',
                            url: ''
                        },
                        {
                            name: 'iPad',
                            url: ''
                        },
                        {
                            name: 'iPhone',
                            url: ''
                        },
                        {
                            name: 'Watch',
                            url: ''
                        },
                        {
                            name: 'AirPods',
                            url: ''
                        },
                        {
                            name: 'TV & Home',
                            url: ''
                        },
                        {
                            name: 'AirTag',
                            url: ''
                        },
                        {
                            name: 'Accessories',
                            url: ''
                        },
                        {
                            name: 'Gift Cards',
                            url: ''
                        }
                    ]
                },
                {
                    subtitle: 'Services',
                    links: [
                        {
                            name: 'Apple Music',
                            url: ''
                        },
                        {
                            name: 'Apple TV+',
                            url: ''
                        },
                        {
                            name: 'Apple Fitness+',
                            url: ''
                        },
                        {
                            name: 'Apple News+',
                            url: ''
                        },
                        {
                            name: 'Apple Arcade',
                            url: ''
                        },
                        {
                            name: 'iCloud',
                            url: ''
                        },
                        {
                            name: 'Apple One',
                            url: ''
                        },
                        {
                            name: 'Apple Card',
                            url: ''
                        },
                        {
                            name: 'Apple Books',
                            url: ''
                        },
                        {
                            name: 'Apple Podcasts',
                            url: ''
                        },
                        {
                            name: 'App Store',
                            url: ''
                        }
                    ]
                },          
                {
                    subtitle: 'Account',
                    links: [
                        {
                            name: 'Manage Your Apple ID',
                            url: ''
                        },
                        {
                            name: 'Apple Store Account',
                            url: ''
                        },
                        {
                            name: 'iCloud.com',
                            url: ''
                        }
                    ]
                },
                {
                    subtitle: 'Apple Store',
                    links: [
                        {
                            name: 'Find a Store',
                            url: ''
                        },
                        {
                            name: 'Genius Bar',
                            url: ''
                        },
                        {
                            name: 'Today at Apple',
                            url: ''
                        },
                        {
                            name: 'Apple Camp',
                            url: ''
                        },
                        {
                            name: 'Apple Store App',
                            url: ''
                        },
                        {
                            name: 'Refurbished and Clearance',
                            url: ''
                        },
                        {
                            name: 'Financing',
                            url: ''
                        },
                        {
                            name: 'Apple Trade In',
                            url: ''
                        },
                        {
                            name: 'Order Status',
                            url: ''
                        },
                        {
                            name: 'Shopping Help',
                            url: ''
                        }
                    ]
                },
                {
                    subtitle: 'For Business',
                    links: [
                        {
                            name: 'Apple and Business',
                            url: ''
                        },
                        {
                            name: 'Shop for Business',
                            url: ''
                        }
                    ]
                },
                {
                    subtitle: 'For Education',
                    links: [
                        {
                            name: 'Apple and Education',
                            url: ''
                        },
                        {
                            name: 'Shop for K-12',
                            url: ''
                        },
                        {
                            name: 'Shop for College',
                            url: ''
                        }
                    ]
                },
                {
                    subtitle: 'For Healthcare',
                    links: [
                        {
                            name: 'Apple in Healthcare',
                            url: ''
                        },
                        {
                            name: 'Health on Apple Watch',
                            url: ''
                        },
                        {
                            name: 'Health Records on iPhone',
                            url: ''
                        }
                    ]
                },
                {
                    subtitle: 'For Government',
                    links: [
                        {
                            name: 'Shop for Government',
                            url: ''
                        },
                        {
                            name: 'Shop for Veterans and Military',
                            url: ''
                        },
                    ]
                },
                {
                    subtitle: 'For Business',
                    links: [
                        {
                            name: 'Accessibility',
                            url: ''
                        },
                        {
                            name: 'Education',
                            url: ''
                        },
                        {
                            name: 'Environment',
                            url: ''
                        },
                        {
                            name: 'Inclusion and Diversity',
                            url: ''
                        },
                        {
                            name: 'Privacy',
                            url: ''
                        },
                        {
                            name: 'Racial Equity and Justice',
                            url: ''
                        },
                        {
                            name: 'Supplier Responsibility',
                            url: ''
                        },
                    ]
                },
                {
                    subtitle: 'About Apple',
                    links: [
                        {
                            name: 'Newsroom',
                            url: ''
                        },
                        {
                            name: 'Apple Leadership',
                            url: ''
                        },
                        {
                            name: 'Career Opportunities',
                            url: ''
                        },
                        {
                            name: 'Investors',
                            url: ''
                        },
                        {
                            name: 'Ethics & Compliance',
                            url: ''
                        },
                        {
                            name: 'Events',
                            url: ''
                        },
                        {
                            name: 'Contact Apple',
                            url: ''
                        },
                    ]
                }
            ],
            footerCopyrights: {
                copyrightShop: 'More ways to shop: <a href="">Find an Apple Store</a> or <a href="">other retailer</a> near you. Or call 1-800-MY-APPLE.',
                copyrightLegal: {
                    info: `Copyright © ${new Date().getFullYear()} Apple Inc. All rights reserved.`,
                    list: [
                        {
                            name: 'Privacy Policy',
                            url: ''
                        },
                        {
                            name: 'Terms of Use',
                            url: ''
                        },
                        {
                            name: 'Sales and Refunds',
                            url: ''
                        },
                        {
                            name: 'Legal',
                            url: ''
                        },
                        {
                            name: 'Site Map',
                            url: ''
                        }
                    ]
                },
            },
            localeLink: {
                name: 'United States',
                url: 'https://www.apple.com/choose-country-region/'
            }
        }
    }
}

</script>

<style lang="scss" scoped>

.footer {
    width: 100%;
    background: #F5F5F7;
    padding: 20px 0;

    .row {
        flex-direction: column;
        row-gap: 25px;
    }

    .footer__column-list {
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        column-gap: 30px;
        row-gap: 25px;
        padding-top: 25px;
        margin-top: 15px;
        border-top: 1px solid #d2d2d7;

        .footer__column {
            max-width: max-content;
            width: 100%;
            display: flex;
            flex-direction: column;
            row-gap: 25px;

            .footer__list {
                max-width: max-content;
                width: 100%;
                display: flex;
                flex-direction: column;
                row-gap: 8px;

                &-title {
                    font-size: 11px;
                    font-weight: 600;
                    color: #1d1d1f;
                }

                &-link {
                    font-size: 11px;
                    color: #424245;

                    &:hover {
                        text-decoration: underline;
                    }
                }
            }
        }
    }

    .footer__copyrights {
        width: 100%;
        display: flex;
        flex-direction: column;
        row-gap: 10px;

        .footer__copyright-shop {
            font-size: 12px;
            color: #424245;
        }

        .line {
            width: 100%;
            height: 1px;
            background: #d2d2d7;
        }

        .footer__copyright-legal {
            display: flex;
            justify-content: space-between;
            align-items: center;

            .legal-info {
                font-size: 12px;
                color: #424245;
            }

            .legal__list {
                display: flex;
                align-items: center;
                gap: 8px;
                
                &-item {
                    border-right: 1px solid #d2d2d7;
                    padding-right: 8px;
                }

                li:last-of-type {
                    border-right: 0;
                }

                &-link {
                    font-size: 13px;
                    color: #424245;

                    &:hover {
                        text-decoration: underline;
                    }
                }
            }

            .locale-link {
                font-size: 12px;
                color: #424245;

                &:hover {
                    text-decoration: underline;
                }
            }
        }
    }
}

</style>