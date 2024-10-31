<template>
  <div class="page">
    <h2>Thêm Liên hệ Mới</h2>
    <ContactForm :contact="{}" @submit:contact="handleAddContact" />
  </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/service/contact.service";

export default {
  components: {
    ContactForm,
  },
  data() {
    return {
      message: '', // Thông báo cho người dùng
    };
  },
  methods: {
    async handleAddContact(newContact) {
      try {
        // Gọi API để thêm liên hệ
        await ContactService.create(newContact);
        alert('Liên hệ mới đã được thêm thành công!');
        this.$router.push({ name: "contactbook" });

      } catch (error) {
        console.error(error);
        this.message = 'Đã xảy ra lỗi khi thêm liên hệ mới.';
      }
    },
  },
};
</script>
