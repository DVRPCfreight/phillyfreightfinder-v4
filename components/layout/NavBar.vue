<template>
    <header class="top-0 absolute w-full flex flex-wrap items-center justify-between border-t-8 border-b border-purple bg-gradient-to-r from-purple via-primary to-primary">
        <div class="container mx-auto flex flex-wrap items-center justify-between ">
            <!-- brand content -->
            <div id="logos" class="">
                <div class="hidden sm:inline-block">
                    <DvrpcLogo class="h-14"/>
                </div>
                <Logo class="h-14" />
                <button
                class="cursor-pointer text-xl leading-none px-3 py-1 rounded bg-transparent block lg:hidden outline-none focus:outline-none"
                type="button"
                v-on:click="toggleNavbar()"
                >
                    <svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" style="fill: #fff"><path d="M24 6h-24v-4h24v4zm0 4h-24v4h24v-4zm0 8h-24v4h24v-4z"/></svg>
                </button>
            </div>
            <!-- begin nav elements -->
            <nav 
            class="lg:flex flex-grow items-center"
            :class="{'hidden': !showMenu, 'block': showMenu}"
            >
                <ul class="flex flex-col lg:flex-row list-none ml-auto">
                    <li class="nav-item">
                        <a 
                            class="" href="#pablo"
                        >
                            Home
                        </a>
                    </li>
                    <li class="nav-item">
                        <a 
                            class="" href="#pablo"
                        >
                            About
                        </a>
                    </li>
                    <li class="nav-item">
                        <a 
                            class="" href="#pablo"
                        >
                            Tools
                        </a>
                    </li>
                    <li class="nav-item">
                        <a 
                            class="" href="#pablo"
                        >
                            View Map
                        </a>
                    </li> 
                </ul>
            </nav>
        </div>
    </header>
</template>

<script>
import DvrpcLogo from '~/components/ui/logos/DvrpcLogo'
import Logo from '~/components/ui/logos/Logo'
export default {
    components: {
        DvrpcLogo,
        Logo
    },
    data () {
        return {
            showMenu: false
        }
    },
    methods: {
        toggleNavbar: function () {
            this.showMenu = !this.showMenu;
        }
    }
}
</script>

<style scoped>
#logos svg{
    filter: drop-shadow(0.15rem 0.15rem 0.1rem rgba(0, 0, 0, 0.5));
    display:inline-block
}

.nav-item > a {
    @apply mx-3 pt-2 pb-0.5 flex items-center text-sm font-light leading-snug text-white border-opacity-0 border-purple border-b-2 hover:border-opacity-100 hover:text-ltblue
}
</style>
