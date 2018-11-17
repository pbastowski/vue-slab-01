<template>
    <v-app>
        <link
            href="https://fonts.googleapis.com/css?family=Roboto:100,300,400,500,700,900|Material+Icons"
            rel="stylesheet"
        />

        <v-toolbar app>
            <v-toolbar-side-icon></v-toolbar-side-icon>
            <v-toolbar-title>Title</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-icon>person</v-icon>
            <v-toolbar-items class="hidden-sm-and-down">
                <v-btn flat>Link One</v-btn>
                <v-btn flat>Link Two</v-btn>
                <v-btn flat>Link Three</v-btn>
            </v-toolbar-items>
        </v-toolbar>

        <v-navigation-drawer Xpermanent app> Drawer </v-navigation-drawer>

        <v-content>
            <v-container fluid> <nuxt /> </v-container>
        </v-content>
    </v-app>
</template>

<style>
[b1],
.b1 {
    border: 1px dashed red;
}
</style>
