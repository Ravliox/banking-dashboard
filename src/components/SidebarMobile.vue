<template>
  <div id="sidebar-mobile" :class="{'retracted': sidebar.hidden, 'rendered': sidebar.rendered}">
    <div class="overlay" @click.stop="retractSideBar()"/>
    <div class="side-container">
        <div class="links">
            <p class="logo">BFS<sup>4e</sup></p>
            <button @click="selectNewLink(link)" class="link" :class="{'selected': link.selected}" v-for="(link, index) in links" :key="index">
                <v-icon size="32" color="#425042">{{link.icon}}</v-icon>
                <p>{{link.label}}</p>
            </button>
        </div>
        <div class="settings">
            <button class="setting">
                <v-icon size="32" color="#7B7B7B">mdi-cog</v-icon>
                <p>Settings</p>
            </button>
            <button class="setting">
                <v-icon size="32" color="#7B7B7B">mdi-logout</v-icon>
                <p>Logout</p>
            </button>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    props: [
      'sidebar'  
    ],
    data() {
        return {
            isRetracted: false,
            links: [
                {
                    label: "Home",
                    icon: 'mdi-home-outline',
                    selected: true 
                },
                {
                    label: "Profile",
                    icon: 'mdi-account-outline',
                    selected: false
                },
                {
                    label: "Wallet",
                    icon: 'mdi-wallet-outline',
                    selected: false
                },
                {
                    label: "Reports",
                    icon: 'mdi-chart-bell-curve-cumulative',
                    selected: false
                },
                {
                    label: "Transactions",
                    icon: 'mdi-swap-horizontal-bold',
                    selected: false
                }
            ]
        }
    },
    methods: {
        selectNewLink(newLink) {
            let oldLink = this.links.find(link => link.selected === true);
            oldLink.selected = false;
            newLink.selected = true;
        },
        retractSideBar() {
            console.log("click");
            this.$emit("retractSidebar");
        }
    }
}
</script>

<style lang="scss">
#sidebar-mobile {
    position: fixed;
    width: 100vw;
    height: 100vh;
    left: 0;
    top: 0;
    background-color: transparent;
    z-index: -1;
    overflow: hidden;
    border-right: none;
    display: flex;

    &.rendered {
        z-index: 99;
    }

    &.retracted {
        .side-container {
            transform: translateX(275px);
        }

        .overlay {
            opacity: 0;
        }
    }

    .side-container {
        position: absolute;
        height: 100%;
        right: 0;
        transform: translateX(0px);
        display: flex;
        width: 275px;
        padding-top: 0.5em;
        padding-bottom: 2em;
        flex-direction: column;
        justify-content: space-between;
        border-right: 1px solid gray;
        z-index: 95;
        background-color: #fff;
        transition: 0.2s transform;

        .logo {
            text-align: center;
            font-size: 2.5em;
        }
    }

    .overlay {
        background-color: rgb(33, 33, 33);
        border-color: rgb(33, 33, 33);
        opacity: 0.5;
        width: 110vw;
        height: 110vh;
        position: fixed;
        left: -10px;
        top: -50px;
        z-index: 90;
        transition: 0.2s opacity;
    }

    .link {
        display: flex;
        width: 8.6em;
        margin-left: 1em;
        padding-left: 1em;
        border-radius: 31px;
        height: 2em;
        align-items: center;
        box-sizing: border-box;
        cursor: pointer;
        transition: 0.2s width;

        &:not(:first-child) {
            margin-top: 0.7em;
        }

        &:hover, &:focus {
            outline: 0;
            background-color: #F8F8F8;
        }

        &.selected {
            border: 2px solid #045E07;
            background-color: #F8F8F8;

            i {
                position: relative;
                right: 2px;
            }

            p {
                font-weight: bold;
            }
        }

        p {
            font-size: 1em;
            margin-left: 0.2em;
            user-select: none;
        }
    }

    .setting {
        display: flex;
        padding-left: 1em;
        align-items: center;

        p {
            margin-left: 0.2em;
            font-size: 0.8em;
            color: #7B7B7B;
        }

        
        &:first-child {
            margin-bottom: 0.8em;
        }

        &:hover, &:focus {
            outline: 0;

            p, i {
                color: #000 !important;
            }
        }
    }
}
</style>