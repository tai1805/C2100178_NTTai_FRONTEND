<template>
    <div v-if="contact" class="page">
        <h4>Hiệu chỉnh Liên hệ</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="addContact"
         
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
    components: {
        ContactForm,
    },
    props: {
        
    },
    data() {
        return {
            contact: {},
            message: "",
        };
    },
    methods: {
        
        async addContact(data) {
            try {
                await ContactService.create(data)
                this.message= "Tao thanh congo";
                 this.$router.push({ name: "ContactBook" });

            }catch (error){
                console.log(error);
            }
        }
    },
    created() {
        // this.getContact(this._id);
        this.message = "";
    },
};
</script>