    <template>
    <h1>Results: {{ reactionTime }} miliseconds</h1>
    <div v-if="reactionTime < 200">
        <p>Fastest hand in the east!!!</p>
    </div>
    <div v-else-if="reactionTime < 400">
        <p>Meh... That's all you got?</p>
    </div>
    <div v-else>
        <p>Breaking news! Something slower than the Internet Explorer has appeared!!</p>
    </div>
    </template>

    <script>
    export default {
    props: ["reactionTime"],
    };
    </script>

    <style>
    </style>