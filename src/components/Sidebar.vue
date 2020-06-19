<template>
  <div id="sidebar" :class="{'retracted': isRetracted}">
      <div class="links">
        <button class="menu-trigger" @click="retractSideBar()"><v-icon size="48">mdi-chevron-left</v-icon></button>
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
</template>

<script>
export default {
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
            this.isRetracted = !this.isRetracted;
        }
    }
}
</script>

<style lang="scss">
#sidebar {
    width: 11em;
    height: calc(100% - 50px);
    padding-top: 1.5em;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border-right: 1px solid gray;
    position: relative;
    transition: 0.3s width;

    &.retracted {
        width: calc(2em + 37px); 
        overflow: hidden;

        .menu-trigger {
            transform: rotate(180deg);
        }

        .link {
            width: calc(2em + 32px);

            p {
                display: none;
            }
        }

        .setting {
            p {
                display: none;
            }
        }
    }
}

.menu-trigger {
    position: absolute;
    top: 0;
    right: 0;

    &:focus, &:hover {
        outline: 0;
        i {
            color: #000 !important;
        }
    }
}

.link {
    display: flex;
    width: 8.3em;
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
</style>