<template>
    <div class="ion-page">
        <ion-header>
            <ion-toolbar>
                <ion-title>ZipInfo</ion-title>
            </ion-toolbar>
        </ion-header>
        <ion-content class="ion-padding">
            <ZipSearch v-on:get-zip="getZipInfo"/>
            <ZipData v-bind:zipData="zipData"/>
            <ClearData v-bind:zipData="zipData" v-on:clear-data="clearData"/>
        </ion-content>
    </div>
</template>

<script>
    import ZipSearch from '../components/ZipSearch';
    import ZipData from '../components/ZipData';
    import ClearData from '../components/ClearData';

    export default {
        name: 'home',
        components: {ZipSearch, ZipData, ClearData},
        data() {
            return {
                zipData: null
            }
        },
        methods: {
            async getZipInfo(zip) {
                const res = await fetch(`https://api.zippopotam.us/us/${zip}`)

                if (res.status == 404) {
                    this.showAlert();
                }

                this.zipData = await res.json();

            },
            clearData() {
                this.zipData = null;
            },
            showAlert() {
                return this.$ionic.alertController.create({
                    header: "Not Valid",
                    message: "Please enter a valid US zipcode",
                    buttons: ['Ok']
                }).then(a => a.present())
            }
        }
    }
</script>
