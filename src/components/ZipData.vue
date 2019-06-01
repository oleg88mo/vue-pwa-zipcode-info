<template>
    <ion-card v-if="zipData">
        <ion-card-header>
            <ion-card-subtitle>{{zipData['post code']}}</ion-card-subtitle>
            <ion-card-title>{{zipData['places'][0]['place name']}}</ion-card-title>
        </ion-card-header>
        <ion-card-content>
            <ion-list>
                <ion-item>
                    <ion-label>
                        <strong>State:</strong>
                        {{zipData['places'][0]['state']}} ({{zipData['places'][0]['state abbreviation']}})
                    </ion-label>
                </ion-item>
                <ion-item>
                    <ion-label>
                        <strong>Latitude:</strong>
                        {{zipData['places'][0]['latitude']}}
                    </ion-label>
                </ion-item>
                <ion-item>
                    <ion-label>
                        <strong>Longitude:</strong>
                        {{zipData['places'][0]['longitude']}}
                    </ion-label>
                </ion-item>
            </ion-list>
        </ion-card-content>
    </ion-card>
</template>

<script>
    export default {
        name: "ZipData",
        props: ["zipData"]
    }
</script>