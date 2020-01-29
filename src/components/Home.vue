<template>
    <div>
        <v-dialog v-model="dialog" max-width="500">
            <v-card class="pt-4" style="text-align: center;">
                <v-container>
                    <v-card-title style="margin-left: 10px; margin-bottom: 25px;" v-if="dialogRouteArr.length == 0">Coming Soon</v-card-title>
                    <v-card-title style="margin-left: 10px; margin-bottom: 25px;" v-else>Please Select</v-card-title>
                    <v-layout row wrap class="pb-3" align-center>
                        <v-flex xs12 sm12 md12 lg12 v-for="(item, key) in dialogRouteArr" :key="key">
                            <v-btn large class="nav-text white--text mb-4" style="text-transform: capitalize; font-weight: 600; " :color="item.color" @click="navigate(item.routeNav)">{{item.routeTitle}}</v-btn>
                        </v-flex>
                    </v-layout>
                </v-container>
            </v-card>
        </v-dialog>
        <div id="kindergarden" style="margin-top: 100px; margin-bottom: 50px;" :style="{marginLeft: page_margin_left_and_right + '%', marginRight: page_margin_left_and_right + '%'}">
            <div style="width: 100%; text-align: left;">
                <h2>Kindergarden Learning Materials</h2>
                <p>These are the related learning materials for kindergarden students.</p>
                <v-container fluid grid-list-xl class="" style="padding-left: 0px!important; padding-right: 0px!important;">
                    <v-layout row wrap>
                        <v-flex xs12 sm12 md6 lg4 d-flex v-for="(item, index) in kinderGardenCourseList" :key="index">
                            <v-hover>
                                <v-card style="border-radius: 7px; min-height: 300px; margin-bottom: 20px; cursor: pointer;" class="pb-4 normal-card" slot-scope="{ hover }" :class="`elevation-${hover ? 12 : 1}`">
                                    <div @click="openDialog(item.route)">
                                        <v-toolbar flat :style="{background: item.color}" style="border-top-left-radius: 7px; border-top-right-radius: 7px;">
                                            <v-toolbar-items>
                                                <v-icon color="white" medium>{{item.icon}}</v-icon>
                                            </v-toolbar-items>
                                            <v-spacer></v-spacer>
                                            <h3 style="color: white; font-size: 16px; line-height: 25px; ">{{item.hours}}</h3>
                                        </v-toolbar>
                                        <v-card-title>
                                            <div style="padding-top: 10px; padding-left: 10px; padding-right: 10px; text-align: left;">
                                                <h3 style="text-align: left; color: #7c8b8e; font-size: 16px; line-height: 25px; ">{{item.type}}</h3>
                                                <h2 style="margin-top: 5px; text-align: left; font-size: 21px; line-height: 32px; color: #374047; word-break: break-word">{{item.title}}</h2>
                                                <p style="word-break: break-word; text-align: left; margin-top: 5px;">{{item.description}}</p>
                                                <v-btn outlined :color="item.color" style="margin-top: 10px;">EXPLORE</v-btn>
                                            </div>
                                        </v-card-title>
                                    </div>
                                </v-card>
                            </v-hover>
                        </v-flex>
                    </v-layout>
                </v-container>
            </div>
        </div>
        <div id="grade1" style="margin-top: 50px; margin-bottom: 50px;" :style="{marginLeft: page_margin_left_and_right + '%', marginRight: page_margin_left_and_right + '%'}">
            <div style="width: 100%; text-align: left;">
                <h2>Grade 1 Learning Materials</h2>
                <p>These are the related learning materials for grade 1 students and teachers.</p>
                <v-container fluid grid-list-xl class="" style="padding-left: 0px!important; padding-right: 0px!important;">
                    <v-layout row wrap>
                        <v-flex xs12 sm12 md6 lg4 d-flex v-for="(item, index) in grade1CourseList" :key="index">
                            <v-hover>
                                <v-card style="border-radius: 7px; min-height: 300px; margin-bottom: 20px; cursor: pointer;" class="pb-4 normal-card" slot-scope="{ hover }" :class="`elevation-${hover ? 12 : 1}`">
                                    <div @click="openDialog(item.route)">
                                        <v-toolbar flat :style="{background: item.color}" style="border-top-left-radius: 7px; border-top-right-radius: 7px;">
                                            <v-toolbar-items>
                                                <v-icon color="white" medium>{{item.icon}}</v-icon>
                                            </v-toolbar-items>
                                            <v-spacer></v-spacer>
                                            <h3 style="color: white; font-size: 16px; line-height: 25px; ">{{item.hours}}</h3>
                                        </v-toolbar>
                                        <v-card-title>
                                            <div style="padding-top: 10px; padding-left: 10px; padding-right: 10px; text-align: left;">
                                                <h3 style="text-align: left; color: #7c8b8e; font-size: 16px; line-height: 25px; ">{{item.type}}</h3>
                                                <h2 style="margin-top: 5px; text-align: left; font-size: 21px; line-height: 32px; color: #374047; word-break: break-word">{{item.title}}</h2>
                                                <p style="word-break: break-word; text-align: left; margin-top: 5px;">{{item.description}}</p>
                                                <v-btn outlined :color="item.color" style="margin-top: 10px;">EXPLORE</v-btn>
                                            </div>
                                        </v-card-title>
                                    </div>
                                </v-card>
                            </v-hover>
                        </v-flex>
                    </v-layout>
                </v-container>
            </div>
        </div>
        <div id="grade2" style="margin-top: 50px; margin-bottom: 50px;" :style="{marginLeft: page_margin_left_and_right + '%', marginRight: page_margin_left_and_right + '%'}">
            <div style="width: 100%; text-align: left;">
                <h2>Grade 2 Learning Materials</h2>
                <p>These are the related learning materials for grade 2 students and teachers.</p>
                <v-container fluid grid-list-xl class="" style="padding-left: 0px!important; padding-right: 0px!important;">
                    <v-layout row wrap>
                        <v-flex xs12 sm12 md6 lg4 d-flex v-for="(item, index) in grade2CourseList" :key="index">
                            <v-hover>
                                <v-card style="border-radius: 7px; min-height: 300px; margin-bottom: 20px; cursor: pointer;" class="pb-4 normal-card" slot-scope="{ hover }" :class="`elevation-${hover ? 12 : 1}`">
                                    <div @click="openDialog(item.route)">
                                        <v-toolbar flat :style="{background: item.color}" style="border-top-left-radius: 7px; border-top-right-radius: 7px;">
                                            <v-toolbar-items>
                                                <v-icon color="white" medium>{{item.icon}}</v-icon>
                                            </v-toolbar-items>
                                            <v-spacer></v-spacer>
                                            <h3 style="color: white; font-size: 16px; line-height: 25px; ">{{item.hours}}</h3>
                                        </v-toolbar>
                                        <v-card-title>
                                            <div style="padding-top: 10px; padding-left: 10px; padding-right: 10px; text-align: left;">
                                                <h3 style="text-align: left; color: #7c8b8e; font-size: 16px; line-height: 25px; ">{{item.type}}</h3>
                                                <h2 style="margin-top: 5px; text-align: left; font-size: 21px; line-height: 32px; color: #374047; word-break: break-word;">{{item.title}}</h2>
                                                <p style="word-break: break-word; text-align: left; margin-top: 5px;">{{item.description}}</p>
                                                <v-btn outlined :color="item.color" style="margin-top: 10px;">EXPLORE</v-btn>
                                            </div>
                                        </v-card-title>
                                    </div>
                                </v-card>
                            </v-hover>
                        </v-flex>
                    </v-layout>
                </v-container>
            </div>
        </div>
        <div id="grade3" style="margin-top: 50px; margin-bottom: 50px;" :style="{marginLeft: page_margin_left_and_right + '%', marginRight: page_margin_left_and_right + '%'}">
            <div style="width: 100%; text-align: left;">
                <h2>Grade 3 Learning Materials</h2>
                <p>These are the related learning materials for grade 3 students and teachers.</p>
                <v-container fluid grid-list-xl class="" style="padding-left: 0px!important; padding-right: 0px!important;">
                    <v-layout row wrap>
                        <v-flex xs12 sm12 md6 lg4 d-flex v-for="(item, index) in grade3CourseList" :key="index">
                            <v-hover>
                                <v-card style="border-radius: 7px; min-height: 300px; margin-bottom: 20px; cursor: pointer;" class="pb-4 normal-card" slot-scope="{ hover }" :class="`elevation-${hover ? 12 : 1}`">
                                    <div @click="openDialog(item.route)">
                                        <v-toolbar flat :style="{background: item.color}" style="border-top-left-radius: 7px; border-top-right-radius: 7px;">
                                            <v-toolbar-items>
                                                <v-icon color="white" medium>{{item.icon}}</v-icon>
                                            </v-toolbar-items>
                                            <v-spacer></v-spacer>
                                            <h3 style="color: white; font-size: 16px; line-height: 25px; ">{{item.hours}}</h3>
                                        </v-toolbar>
                                        <v-card-title>
                                            <div style="padding-top: 10px; padding-left: 10px; padding-right: 10px; text-align: left;">
                                                <h3 style="text-align: left; color: #7c8b8e; font-size: 16px; line-height: 25px; ">{{item.type}}</h3>
                                                <h2 style="margin-top: 5px; text-align: left; font-size: 21px; line-height: 32px; color: #374047; word-break: break-word;">{{item.title}}</h2>
                                                <p style="word-break: break-word; text-align: left; margin-top: 5px;">{{item.description}}</p>
                                                <v-btn outlined :color="item.color" style="margin-top: 10px;">EXPLORE</v-btn>
                                            </div>
                                        </v-card-title>
                                    </div>
                                </v-card>
                            </v-hover>
                        </v-flex>
                    </v-layout>
                </v-container>
            </div>
        </div>
        <div id="grade4" style="margin-top: 50px; margin-bottom: 50px;" :style="{marginLeft: page_margin_left_and_right + '%', marginRight: page_margin_left_and_right + '%'}">
            <div style="width: 100%; text-align: left;">
                <h2>Grade 4 Learning Materials</h2>
                <p>These are the related learning materials for grade 4 students and teachers.</p>
                <v-container fluid grid-list-xl class="" style="padding-left: 0px!important; padding-right: 0px!important;">
                    <v-layout row wrap>
                        <v-flex xs12 sm12 md6 lg4 d-flex v-for="(item, index) in grade4CourseList" :key="index">
                            <v-hover>
                                <v-card style="border-radius: 7px; min-height: 300px; margin-bottom: 20px; cursor: pointer;" class="pb-4 normal-card" slot-scope="{ hover }" :class="`elevation-${hover ? 12 : 1}`">
                                    <div @click="openDialog(item.route)">
                                        <v-toolbar flat :style="{background: item.color}" style="border-top-left-radius: 7px; border-top-right-radius: 7px;">
                                            <v-toolbar-items>
                                                <v-icon color="white" medium>{{item.icon}}</v-icon>
                                            </v-toolbar-items>
                                            <v-spacer></v-spacer>
                                            <h3 style="color: white; font-size: 16px; line-height: 25px; ">{{item.hours}}</h3>
                                        </v-toolbar>
                                        <v-card-title>
                                            <div style="padding-top: 10px; padding-left: 10px; padding-right: 10px; text-align: left;">
                                                <h3 style="text-align: left; color: #7c8b8e; font-size: 16px; line-height: 25px; ">{{item.type}}</h3>
                                                <h2 style="margin-top: 5px; text-align: left; font-size: 21px; line-height: 32px; color: #374047; word-break: break-word">{{item.title}}</h2>
                                                <p style="word-break: break-word; text-align: left; margin-top: 5px;">{{item.description}}</p>
                                                <v-btn outlined :color="item.color" style="margin-top: 10px;">EXPLORE</v-btn>
                                            </div>
                                        </v-card-title>
                                    </div>
                                </v-card>
                            </v-hover>
                        </v-flex>
                    </v-layout>
                </v-container>
            </div>
        </div>
        <div id="grade5" style="margin-top: 50px; margin-bottom: 50px;" :style="{marginLeft: page_margin_left_and_right + '%', marginRight: page_margin_left_and_right + '%'}">
            <div style="width: 100%; text-align: left;">
                <h2>Grade 5 Learning Materials</h2>
                <p>These are the related learning materials for grade 5 students and teachers.</p>
                <v-container fluid grid-list-xl class="" style="padding-left: 0px!important; padding-right: 0px!important;">
                    <v-layout row wrap>
                        <v-flex xs12 sm12 md6 lg4 d-flex v-for="(item, index) in grade5CourseList" :key="index">
                            <v-hover>
                                <v-card style="border-radius: 7px; min-height: 300px; margin-bottom: 20px; cursor: pointer;" class="pb-4 normal-card" slot-scope="{ hover }" :class="`elevation-${hover ? 12 : 1}`">
                                    <div @click="openDialog(item.route)">
                                        <v-toolbar flat :style="{background: item.color}" style="border-top-left-radius: 7px; border-top-right-radius: 7px;">
                                            <v-toolbar-items>
                                                <v-icon color="white" medium>{{item.icon}}</v-icon>
                                            </v-toolbar-items>
                                            <v-spacer></v-spacer>
                                            <h3 style="color: white; font-size: 16px; line-height: 25px; ">{{item.hours}}</h3>
                                        </v-toolbar>
                                        <v-card-title>
                                            <div style="padding-top: 10px; padding-left: 10px; padding-right: 10px; text-align: left;">
                                                <h3 style="text-align: left; color: #7c8b8e; font-size: 16px; line-height: 25px; ">{{item.type}}</h3>
                                                <h2 style="margin-top: 5px; text-align: left; font-size: 21px; line-height: 32px; color: #374047; word-break: break-word">{{item.title}}</h2>
                                                <p style="word-break: break-word; text-align: left; margin-top: 5px;">{{item.description}}</p>
                                                <v-btn outlined :color="item.color" style="margin-top: 10px;">EXPLORE</v-btn>
                                            </div>
                                        </v-card-title>
                                    </div>
                                </v-card>
                            </v-hover>
                        </v-flex>
                    </v-layout>
                </v-container>
            </div>
        </div>
        <div id="grade6" style="margin-top: 50px; margin-bottom: 50px;" :style="{marginLeft: page_margin_left_and_right + '%', marginRight: page_margin_left_and_right + '%'}">
            <div style="width: 100%; text-align: left;">
                <h2>Grade 6 Learning Materials</h2>
                <p>These are the related learning materials for grade 6 students and teachers.</p>
                <v-container fluid grid-list-xl class="" style="padding-left: 0px!important; padding-right: 0px!important;">
                    <v-layout row wrap>
                        <v-flex xs12 sm12 md6 lg4 d-flex v-for="(item, index) in grade6CourseList" :key="index">
                            <v-hover>
                                <v-card style="border-radius: 7px; min-height: 300px; margin-bottom: 20px; cursor: pointer;" class="pb-4 normal-card" slot-scope="{ hover }" :class="`elevation-${hover ? 12 : 1}`">
                                    <div @click="openDialog(item.route)">
                                        <v-toolbar flat :style="{background: item.color}" style="border-top-left-radius: 7px; border-top-right-radius: 7px;">
                                            <v-toolbar-items>
                                                <v-icon color="white" medium>{{item.icon}}</v-icon>
                                            </v-toolbar-items>
                                            <v-spacer></v-spacer>
                                            <h3 style="color: white; font-size: 16px; line-height: 25px; ">{{item.hours}}</h3>
                                        </v-toolbar>
                                        <v-card-title>
                                            <div style="padding-top: 10px; padding-left: 10px; padding-right: 10px; text-align: left;">
                                                <h3 style="text-align: left; color: #7c8b8e; font-size: 16px; line-height: 25px; ">{{item.type}}</h3>
                                                <h2 style="margin-top: 5px; text-align: left; font-size: 21px; line-height: 32px; color: #374047; word-break: break-word">{{item.title}}</h2>
                                                <p style="word-break: break-word; text-align: left; margin-top: 5px;">{{item.description}}</p>
                                                <v-btn outlined :color="item.color" style="margin-top: 10px;">EXPLORE</v-btn>
                                            </div>
                                        </v-card-title>
                                    </div>
                                </v-card>
                            </v-hover>
                        </v-flex>
                    </v-layout>
                </v-container>
            </div>
        </div>
        <div id="others" style="margin-top: 50px; margin-bottom: 50px;" :style="{marginLeft: page_margin_left_and_right + '%', marginRight: page_margin_left_and_right + '%'}">
            <div style="width: 100%; text-align: left;">
                <h2>Other Related Learning Materials</h2>
                <p>These are some related learning materials for students and teachers.</p>
                <v-container fluid grid-list-xl class="" style="padding-left: 0px!important; padding-right: 0px!important;">
                    <v-layout row wrap>
                        <v-flex xs12 sm12 md6 lg4 d-flex v-for="(item, index) in otherCourseList" :key="index">
                            <v-hover>
                                <v-card style="border-radius: 7px; min-height: 300px; margin-bottom: 20px; cursor: pointer;" class="pb-4 normal-card" slot-scope="{ hover }" :class="`elevation-${hover ? 12 : 1}`">
                                    <div @click="openDialog(item.route)">
                                        <v-toolbar flat :style="{background: item.color}" style="border-top-left-radius: 7px; border-top-right-radius: 7px;">
                                            <v-toolbar-items>
                                                <v-icon color="white" medium>{{item.icon}}</v-icon>
                                            </v-toolbar-items>
                                            <v-spacer></v-spacer>
                                            <h3 style="color: white; font-size: 16px; line-height: 25px; ">{{item.hours}}</h3>
                                        </v-toolbar>
                                        <v-card-title>
                                            <div style="padding-top: 10px; padding-left: 10px; padding-right: 10px; text-align: left;">
                                                <h3 style="text-align: left; color: #7c8b8e; font-size: 16px; line-height: 25px; ">{{item.type}}</h3>
                                                <h2 style="margin-top: 5px; text-align: left; font-size: 21px; line-height: 32px; color: #374047; word-break: break-word">{{item.title}}</h2>
                                                <p style="word-break: break-word; text-align: left; margin-top: 5px;">{{item.description}}</p>
                                                <v-btn outlined :color="item.color" style="margin-top: 10px;">EXPLORE</v-btn>
                                            </div>
                                        </v-card-title>
                                    </div>
                                </v-card>
                            </v-hover>
                        </v-flex>
                    </v-layout>
                </v-container>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
            page_margin_left_and_right: 10, 
            windowWidth: 0,
            dialog: false,
            dialogRouteArr: [],
            kinderGardenCourseList: [
                {title: 'Animal Bingo', description: 'Students will engage in shape and color recognition, match and count animals, and learn to follow instructions in a fun and engaging way.', type: 'Roboric Course', color: '#ee6e00', icon: 'settings_applications', hours: '2 hours', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/build-social-skills-together-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/animal-bingo-student'}]},
                {title: 'Duplo Creative Bricks', description: 'The Duplo Creative Bricks is what every young designer needs. This set enabling children to learn the most basic part of connecting different bricks.', type: 'Robotic Course', color: '#ee6e00', icon: 'settings_applications', hours: '3 hours', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/build-social-skills-together-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/duplo-creative-bricks-student'}]},
                {title: 'Math Train', description: 'Designed for preschool children, the Math Train Set uses a relevant theme which naturally incorporates math.', type: 'Robotic Course', color: '#afca0b', icon: 'settings_applications', hours: '4 hours', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/math-train-teacher'}, {color: '#56aadc', routeTitle: 'Teacher Lessons Plan', routeNav: 'https://education.lego.com/en-us/lessons/preschool-math-train'}]},
                {title: 'Café +', description: 'Designed for preschool children, the café theme naturally incorporates math, enabling children to explore math-related concepts as they build café items in a familiar setting', type: 'Robotic Course', color: '#afca0b', icon: 'settings_applications', hours: '3.5 hours', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/cafe-exploration-teacher'}, {color: '#56aadc', routeTitle: 'Teacher Lessons Plan', routeNav: 'https://education.lego.com/en-us/lessons?Products=Caf%C3%A9%2B&pagesize=12'}]},
                {title: 'Story Tales', description: ' As children work together to build scenes, they will explore common literary elements, such as settings, characters, and events.', type: 'Robotic Course', color: '#afca0b', icon: 'settings_applications', hours: '4 hours', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/story-tales-teacher'}, {color: '#56aadc', routeTitle: 'Teacher Lessons Plan', routeNav: 'https://education.lego.com/en-us/lessons?Products=StoryTales%20Set&pagesize=12'}]},
                {title: 'Build Me Emotions', description: ' Each lesson addresses a typical preschool scenario in which children learn about their own feelings and preferences as well as those of others.', type: 'Robotic Course', color: '#afca0b', icon: 'settings_applications', hours: '7 hours', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/build-me-emotions-teacher'}, {color: '#56aadc', routeTitle: 'Teacher Lessons Plan', routeNav: 'https://education.lego.com/en-us/lessons?Products=Build%20Me%20%22Emotions%22&pagesize=12'}]},
                {title: 'Playground', description: 'The set is great for exploring people, communities and leisure activities - and the number tiles that are included are useful for early numeracy teaching.', type: 'Robotic Course', color: '#afca0b', icon: 'settings_applications', hours: 'TBC', route: []},
                {title: 'Creative Builder', description: 'the set is designed to encourage collaboration and storytelling, and helps to develop the use of descriptive language and an understanding of different roles and emotions that relate to community life.', type: 'Robotic Course', color: '#afca0b', icon: 'settings_applications', hours: 'TBC', route: []},
                {title: 'Early Simple Machines', description: 'The ‘Early Simple Machines’ curriculum pack enables you to partially cover the following Crosscutting Concepts and overall Science and Engineering Practices', type: 'Robotic Course', color: '#fb5d4a', icon: 'settings_applications', hours: '6 hours', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/early-simple-machines-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/early-simple-machines-student'}]},
                {title: 'Early Structures Set', description: 'This set provides building ideas for 12 different structures, such as bridges and towers, as well as inspiration for four additional problem-solving models.', type: 'Robotic Course', color: '#fb5d4a', icon: 'settings_applications', hours: 'TBC', route: [], }
            ],
            grade1CourseList: [
                {title: 'Intro to RQ Robot', description: 'It is important to understand the main function of RQ robot before starting to the RQ core syllabus', type: 'Robotic Course', color: '#56aadc', icon: 'settings_applications', hours: '56 minutes', route: [{routeNav: 'https://anfalschooledu.web.app/rq-robot-introduction'}]},
                {title: 'Grade 1 RQ110', description: 'This is a robotics course taught by using syllabus RQ110 specifically designed for Grade 1 students', type: 'Robotic Course', color: '#56aadc', icon: 'settings_applications', hours: '5 hours', route: [{routeNav: 'https://anfalschooledu.web.app/rq110-robot-grade1'}]},
                {title: 'Understand Human Body Parts', description: 'This 3D printing course is to let students understand about body parts by visualizing.', type: '3D Prining Course', color: '#7a35e8', icon: 'category', hours: '2 hours', route: [{color: '#b14986', routeTitle: '3D Print Human Head', routeNav: 'https://www.thingiverse.com/thing:90531'}, {color: '#56aadc', routeTitle: '3D Print Human Skeleton', routeNav: 'https://www.thingiverse.com/thing:1528540'}]},
                {title: 'STEM Toys', description: 'STEM Toys enabling students to have a basic understanding about structural building and remote control.', type: 'Science Corner', color: '#f734a9', icon: 'group_work', hours: '1 hour', route: []},
                {title: 'Push and Pull Trundle Wheel', description: 'We can make use of the simple mechanism to learn the concept of push and pull by building the Trundle Wheel', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#15'}]},
                {title: 'Speed and Direction with Land Yacht', description: 'This module enabling students to understand the concept of speed and direction with interactive activity.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#20'}]},
                {title: 'Source of Sounds', description: 'This is a 360° video to let student experience different types of sound from the nature.', type: 'Virtual Reality Course', color: '#e89210', icon: '360', hours: '30 minutes', route: [{routeNav: 'https://www.youtube.com/watch?v=jP75Tmkjaa4'}]},
                {title: 'Make a Music Instrument', description: 'This 3D printing course enabling students to observe sounds from different music instrument.', type: '3D Printing Course', color: '#7a35e8', icon: 'category', hours: '2 hours', route: [{routeNav: 'https://www.thingiverse.com/thing:1735985'}]},
            ],
            grade2CourseList: [
                {title: 'Intro to RQ Robot', description: 'It is important to understand the main function of RQ robot before starting to the RQ core syllabus', type: 'Robotic Course', color: '#56aadc', icon: 'settings_applications', hours: '56 minutes', route: [{routeNav: 'https://anfalschooledu.web.app/rq-robot-introduction'}]},
                {title: 'Grade 2 RQ110', description: 'This is a robotics course taught by using syllabus RQ110 specifically designed for Grade 2 students', type: 'Robotic Course', color: '#56aadc', icon: 'settings_applications', hours: '5 hours', route: [{routeNav: 'https://anfalschooledu.web.app/rq110-robot-grade2'}]},
                {title: 'Learn Simple Machines', description: 'This module enabling students to understand how simple machines such as lever, pulley, wheel and axle works.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher#3'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#1'}]},
                {title: 'Learn Mechanism and Structures', description: 'This module enabling students to understand the mechanism and structures.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher#9'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#7'}]},
                {title: 'Learn Electricity with Windmill', description: 'Learn electricity by knowing where the electricity comes from especially the renewable one.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#18'}]},
                {title: 'Different Floor Material with Power Car', description: 'Apply different material on the floor surface that the power car is driving on.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#21'}]},
                {title: 'Different Rocks with Tower Crane', description: 'Teacher could provide the students with different rock and load on the tower crane.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher#14'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#26'}]},
                {title: 'Build Fishing Rod and Learn Animals', description: 'This module enable students to learn different sea animals and build fishing rod with interactive activity.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#12'}]},
                {title: 'Build Dogbot and Learn Animals', description: 'This module enable students to learn the body structure of dog with interactive activity.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#24'}]},
                {title: 'Build Sweeper', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#11'}]},
                {title: 'Build Freewheeling', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#13'}]},
                {title: 'Build The Hammer', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#14'}]},
                {title: 'Build Letter Balance', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#16'}]},
                {title: 'Build Click Clock', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#17'}]},
                {title: 'Build Free Wheeler', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#20'}]},
                {title: 'Build Dragster', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#22'}]},
                {title: 'Build The Walker', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#23'}]},
                {title: 'Build Beam Balance', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#25'}]},
                {title: 'Learn Ramp', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#27'}]},
                {title: 'Learn Gear Racer', description: 'This module enable students to learn simple machines and mechanism.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#28'}]},
            ],
            grade3CourseList: [
                {title: 'Intro to RQ Robot', description: 'It is important to understand the main function of RQ robot before starting to the RQ core syllabus', type: 'Robotic Course', color: '#218ecf', icon: 'settings_applications', hours: '56 minutes', route: [{routeNav: 'https://anfalschooledu.web.app/rq-robot-introduction'}]},
                {title: 'Grade 3 RQ120', description: 'This is a robotics course taught by using syllabus RQ120 specifically designed for Grade 3 students', type: 'Robotic Course', color: '#218ecf', icon: 'settings_applications', hours: '5 hours', route: [{routeNav: 'https://anfalschooledu.web.app/rq120-robot-grade3'}]},
                {title: 'Life Processes with VR', description: 'This is a 360° software to let students experience the beginning of life on earth.', type: 'Science Subject', color: '#b941d1', icon: '360', hours: '45 minutes', route: [{routeNav: 'https://www.microsoft.com/en-us/p/from-slime-to-dinosaurs/9p71t1srs2dn?activetab=pivot:overviewtab'}]},
                {title: 'Learn Material with Boat Pulley', description: 'This module enable students to learn different material attribute such as mass, weight and etc.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/renewable-energy-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/renewable-energy-student#6'}]},
                {title: 'Learn Forces with Hand Generator', description: 'This module introduce different type of forces and kinetic energy.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/renewable-energy-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/renewable-energy-student#1'}]},
                {title: 'Learn Forces in Newton Classroom', description: 'This is a 360° software to let students experience different way of lecturing in Virtual World.', type: 'Science Subject', color: '#b941d1', icon: '360', hours: '45 minutes', route: [{routeNav: 'https://www.microsoft.com/en-us/p/newtons-house-of-forces/9ndzxxvpwd7c?activetab=pivot:overviewtab'}]},
                {title: 'Learn Senses with Solar Station', description: 'Teacher could use this opportunity to introduce about human skin sense and discuss about heat and sunlight for solar energy.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/renewable-energy-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/renewable-energy-student#2'}]},
                {title: 'Learn Senses with Wind Turbine', description: 'Teacher could use this opportunity to introduce about smell and discuss about sense of smell from different non-renewable factory.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/renewable-energy-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/renewable-energy-student#3'}]},
                {title: 'Environment Healthy with Solar Vehicle', description: 'This module introducing environment healthiness by building a solar vehicle and see how solar could help to replace our current vehicle.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/renewable-energy-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/renewable-energy-student#5'}]},
                {title: 'Build a Hydro Turbine', description: 'This module enable students to learn renewable energy.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#4'}]},
                {title: 'Some Principle Models', description: 'This module enable students to learn mechanisms.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '45 minutes', route: [{color: '#b14986', routeTitle: 'Teacher Guidelines', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-teacher'}, {color: '#56aadc', routeTitle: 'Student Building Instructions', routeNav: 'https://anfalschooledu.web.app/machines-and-mechanisms-student#7'}]},
            ],
            grade4CourseList: [
                {title: 'Intro to RQ Robot', description: 'It is important to understand the main function of RQ robot before starting to the RQ core syllabus', type: 'Robotic Course', color: '#218ecf', icon: 'settings_applications', hours: '56 minutes', route: [{routeNav: 'https://anfalschooledu.web.app/rq-robot-introduction'}]},
                {title: 'Grade 4 RQ120', description: 'This is a robotics course taught by using syllabus RQ120 specifically designed for Grade 4 students', type: 'Robotic Course', color: '#218ecf', icon: 'settings_applications', hours: '5 hours', route: [{routeNav: 'https://anfalschooledu.web.app/rq120-robot-grade4'}]},
                {title: 'Understand Human Skeleton', description: 'This 3D printing course is to let students understand about human skeleton by visualizing.', type: '3D Prining Science Subject', color: '#b941d1', icon: 'category', hours: '2 hours', route: [{routeNav: 'https://www.thingiverse.com/thing:1528540'}]},
                {title: 'Understand Animal Skeleton', description: 'This 3D printing course is to let students understand about animal skeleton by visualizing.', type: '3D Prining Science Subject', color: '#b941d1', icon: 'category', hours: '2 hours', route: [{routeNav: 'https://www.thingiverse.com/thing:308335'}]},
                {title: 'Learn Material Changes with Kosmos Air', description: 'Kosmos Air is a pneumatic and hydraulic model which use water power to control the model.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '2 hours', route: []},
                {title: 'Create Circuit with Toys Snap', description: 'Students will learn to create simple circuit by using the tools called Toys Snap.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '2 hours', route: []},
                {title: 'Learn Sound by Making Music Instrument', description: 'This 3D printing course is to let students understand sounds, frequency, amplitude and etc.', type: '3D Prining Science Subject', color: '#b941d1', icon: 'category', hours: '2 hours', route: [{routeNav: 'https://www.thingiverse.com/thing:1735985'}]},
                {title: 'Solar Robot Kit', description: 'This module enable students to build solar related robotic kit.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '14 hours', route: []},
            ],
            grade5CourseList: [
                {title: 'Intro to RQ Robot', description: 'It is important to understand the main function of RQ robot before starting to the RQ core syllabus', type: 'Robotic Course', color: '#0366a1', icon: 'settings_applications', hours: '56 minutes', route: [{routeNav: 'https://anfalschooledu.web.app/rq-robot-introduction'}]},
                {title: 'Grade 5 RQ130', description: 'This is a robotics course taught by using syllabus RQ130 specifically designed for Grade 5 students', type: 'Robotic Course', color: '#0366a1', icon: 'settings_applications', hours: '5 hours', route: [{routeNav: 'https://anfalschooledu.web.app/rq130-robot-grade5'}]},
                {title: 'Learn Plant by Exploring Plant', description: 'This is a 360° video to let students experience the plant internal structure such as plant cell.', type: 'Science Subject', color: '#b941d1', icon: '360', hours: '2 hours', route: [{routeNav: 'https://youtu.be/C-DdsrBNI4s'}]},
                {title: 'Explore our Galaxy', description: 'This is a 360° software to let students experience our galaxy, solar system is one of it.', type: 'Science Subject', color: '#b941d1', icon: '360', hours: '2 hours', route: [{routeNav: 'https://www.microsoft.com/en-us/p/galaxy-explorer/9nblggh4q4jg?'}]},
                {title: 'Build Drone with Airblock', description: 'This module enable students to build drone with the simple modular structure provided by Airblock.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '4 hours', route: []},
            ],
            grade6CourseList: [
                {title: 'Intro to RQ Robot', description: 'It is important to understand the main function of RQ robot before starting to the RQ core syllabus', type: 'Robotic Course', color: '#0366a1', icon: 'settings_applications', hours: '56 minutes', route: [{routeNav: 'https://anfalschooledu.web.app/rq-robot-introduction'}]},
                {title: 'Grade 6 RQ130', description: 'This is a robotics course taught by using syllabus RQ130 specifically designed for Grade 6 students', type: 'Robotic Course', color: '#0366a1', icon: 'settings_applications', hours: '5 hours', route: [{routeNav: 'https://anfalschooledu.web.app/rq130-robot-grade6'}]},
                {title: 'Learn Human Organs by Visualizing', description: 'This 3D printing course is to let students understand about human heart by visualizing.', type: '3D Prining Science Subject', color: '#b941d1', icon: 'category', hours: '2 hours', route: [{routeNav: 'https://www.thingiverse.com/thing:852939'}]},
                {title: 'Smart Home Kit', description: 'This is an Arduino Kit that allows student to build IoT project easily. Student can learn simple programming as well.', type: 'Science Subject', color: '#b941d1', icon: 'group_work', hours: '22 hours', route: [{routeNav: 'https://anfalschooledu.web.app/smart-home-kit'}]},
                {title: 'Build Humanoid Robot', description: 'This module allows student to program the motion and action of a humanoid robot.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '4 hours', route: [{routeNav: 'https://anfalschooledu.web.app/rq-huno'}]},
                {title: 'Learn Hydraulic Arm', description: 'This module allows student to understand the concept of Hydraulic arm.', type: 'Science Corner', color: '#afca0b', icon: 'group_work', hours: '2 hours', route: []},
            ],
            otherCourseList: [
                {title: 'Set up 3D Printer', description: 'This is a guideline to setup 3D Printer or fine tune 3D printer if there is any error happens.', type: '3D Printing Course', color: '#7a35e8', icon: 'category', hours: '2 hours', route: [{routeNav: 'http://www.geeetech.com/Documents/Me%20Creator%202User%20Manual.pdf'}]},
            ]
        }
    },
    methods: {
        navigate (route) {
            window.open(route, '_self')
        },
        openDialog(routeArr) {
            this.dialogRouteArr = []
            this.dialogRouteArr = routeArr
            if (this.dialogRouteArr.length == 1) {
                this.navigate(this.dialogRouteArr[0].routeNav)
            } else {
                this.dialog = true
            }
            
        }
    },
    created () {
        if (window.innerWidth <= 1000) {
            // small screen device
            this.page_margin_left_and_right = 3
            this.windowWidth = window.innerWidth
        } else {
            // big screen device
            this.page_margin_left_and_right = 10
            this.windowWidth = window.innerWidth
        }
    },
    mounted () {
        this.$nextTick(() => {
            window.addEventListener('resize', () => {
                this.windowWidth = window.innerWidth
                
            })
        })
    },
    watch: {
        windowWidth (newWidth, oldWidth) {
            // console.log("New Screen Width is: ", newWidth)
            if (newWidth <= 1000) {
                // small screen device
                this.page_margin_left_and_right = 3
            } else {
                // big screen device
                this.page_margin_left_and_right = 10
            }
        },
    }
}
</script>

<style>

</style>