<template>
    <div>
        <v-app-bar fixed app  color="#3e4750" class="mb-7" dark flat :style="{paddingLeft: page_margin_left_and_right + '%', paddingRight: page_margin_left_and_right + '%'}">
            <v-app-bar-nav-icon color="white" class="hidden-lg-and-up mr-3" @click="navigationDrawer = !navigationDrawer"></v-app-bar-nav-icon>
            <h2 @click="" style="padding-top: 0px; font-weight: 500; letter-spacing: 0px; cursor: pointer;" class="hidden-md-and-down header-logo-dark">ANFAL SCHOOL CLASSROOM</h2>
            <v-spacer></v-spacer>
            <v-menu bottom left>
                <template v-slot:activator="{ on }">
                    <v-btn dark icon v-on="on">
                        <v-icon>filter_list</v-icon>
                    </v-btn>
                </template>

                <v-list>
                    <v-list-item v-for="(item, i) in items" :key="i" @click="$vuetify.goTo(item.id, {duration: scrollDuration, offset: scrollOffset, easing: scrollPattern})">
                        <v-list-item-title>{{ item.title }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
            <!-- <div class="hidden-md-and-down">
                <v-btn flat style="text-transform: capitalize; font-weight: 700!important; font-size: 16px; margin-right: 0!important;" :ripple="false" color="#B2BBBD" @click="$router.push({name: 'library'})">Programs</v-btn>
                <v-btn flat style="text-transform: capitalize; font-weight: 700!important; font-size: 16px; margin-right: 0!important;" :ripple="false" color="#B2BBBD" @click="$router.push({name: 'career'})">Career</v-btn>
                <v-btn flat style="text-transform: capitalize; font-weight: 700!important; font-size: 16px; margin-right: 0!important;" :ripple="false" color="#B2BBBD" @click="$router.push({name: 'enterprise'})">For Enterprise</v-btn>
            </div>
            <v-divider class="hidden-md-and-down mx-3" inset style="margin-top: 10px; margin-bottom: 20px;" vertical color="#B2BBBD"></v-divider>
            <div>
                <v-btn v-if="!isUserLoggedin" flat style="text-transform: capitalize; font-weight: 700!important; font-size: 16px; margin-right: 0!important;" :ripple="false" color="#B2BBBD" @click="$router.push({name: 'login'})">Sign In</v-btn>
                <v-btn v-if="!isUserLoggedin" outline style="text-transform: capitalize; font-weight: 700!important; font-size: 16px; margin-right: 0!important;" :ripple="false" color="#61ca87" @click="$router.push({name: 'signup1'})">Get Started</v-btn>
                <v-btn v-if="isUserLoggedin" depressed style="text-transform: capitalize; font-weight: 700!important; font-size: 16px; margin-right: 0!important;" :ripple="false" color="#61ca87" @click="$router.push({name: 'home'})">My Classroom</v-btn>
            </div> -->
        </v-app-bar>
        
        <v-navigation-drawer v-model="navigationDrawer" absolute temporary dark style="background-color: #3e4750; border-color: #3e4750;">
            <h2 @click="" style="font-weight: 500; font-size: 16px; padding-top: 20px; padding-bottom: 8px; letter-spacing: 2px; cursor: pointer; text-align: left; margin-left: 20px;" class="header-logo-dark">ANFAL SCHOOL CLASSROOM</h2>
            <v-divider class="ma-3" color="white"></v-divider>
            <!-- <v-list-tile v-for="item in navigationList" :key="item.title" @click="$router.push({name: item.route})">
                <v-list-tile-action>
                    <v-icon>{{ item.icon }}</v-icon>
                </v-list-tile-action>

                <v-list-tile-content >
                    <v-list-tile-title style="color: white;">{{ item.title }}</v-list-tile-title>
                </v-list-tile-content>
            </v-list-tile> -->
        </v-navigation-drawer>
    </div>
  
</template>

<script>
export default {
    data: function(){
        return {
            scrollDuration: 1000,
            scrollOffset: -50,
            scrollPattern: 'easeInOutCubic',
            drawer: {
                open: false,
                clipped: false,
                fixed: false,
                permanent: false,
                mini: false
            },
            toolbar: {
                clippedLeft: false,
                fixed: true,
            },
            page_margin_left_and_right: 7, 
            windowWidth: 0,
            offsetX: 0,
            navigationDrawer: false,
            items: [
                {title: 'Kindergarden', id: '#kindergarden'},
                {title: 'Grade 1', id: '#grade1'},
                {title: 'Grade 2', id: '#grade2'},
                {title: 'Grade 3', id: '#grade3'},
                {title: 'Grade 4', id: '#grade4'},
                {title: 'Grade 5', id: '#grade5'},
                {title: 'Grade 6', id: '#grade6'},
                {title: 'Others', id: '#others'},
            ]
        }
    },
    mounted () {
        this.$nextTick(() => {
            window.addEventListener('resize', () => {
                this.windowWidth = window.innerWidth
                this.offsetX = window.pageXOffset
                
            })
        })
    },
    created () {
        if (window.innerWidth <= 1000) {
            // small screen device
            this.page_margin_left_and_right = 0
        } else {
            // big screen device
            this.page_margin_left_and_right = 7
        }
    },
    watch: {
        windowWidth (newWidth, oldWidth) {
            // console.log("New Screen Width is: ", newWidth)
            if (newWidth <= 1000) {
                // small screen device
                this.page_margin_left_and_right = 0
            } else {
                // big screen device
                this.page_margin_left_and_right = 7
            }
        },
    },

}
</script>

<style>
.header-logo-dark {
    color: white;
}
.header-logo-dark:hover {
    color: #5ed180;
}
</style>