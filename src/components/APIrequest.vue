<script>
import axios from "axios";
export default {
    methods: {
        getTask(){
            const request = {
                id: 35,
                list: "testlist",
            };
            axios.post("http://127.0.0.1:5000/get/task", request)
            .then(response => this.$emit('getTask' ,response));
        }
    },
    mounted(){
        this.getTask();
    }

}
</script>

<style>

</style>