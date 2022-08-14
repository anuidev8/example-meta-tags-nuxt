<template>
  <section class="testimonial-section d-flex justify-center align-center">
    <h2>Create project</h2>
   <li class="profile-info-item profile-info-item--name font-weight-bold">{{ testimonialProfile.title }}</li>
   lo
  </section>
</template>
<script>
  export default {


    data() {
      return {
        isAviable: true,
        isLoading: true,
        /* testimonialProfile: {} */
      }
    },
      async asyncData({query,redirect,store,params}) {
      let testimonialProfile = {}
      let {
          id
        } = params


        try {
          if(id){
               const testimonial =  await fetch('https://jsonplaceholder.typicode.com/todos/1')
              const res = await  testimonial.json()
              testimonialProfile = {
                ...res,
                image:'https://cdn.pixabay.com/photo/2021/08/25/07/21/cat-6572630__340.jpg'
              }
              console.log(testimonialProfile );
       /*      if  (testimonial.data.reemper ) {
                  testimonialProfile = testimonial?.data.reemper

        } else {
         redirect('/')
        } */
          }else{
               redirect('/')
          }

        } catch (error) {
         redirect('/')
        }




      return { testimonialProfile }
    },

 /*    computed:{
      testimonial(){
        return this.$store.state.testimonials.testimonial
      }
    }, */
head(){
  return{
      htmlAttrs: {
    lang: "en-GB",
  },
  title: `${this.testimonialProfile.title}-web`,
  meta: [
    { charset: "utf-8" },
    { name: "HandheldFriendly", content: "True" },
    { name: "viewport", content: "width=device-width, initial-scale=1" },
    {
      hid: "description",
      name: "description",
      content:`${this.testimonialProfile.title}`,
    },
    { property: "og:site_name", content: "Redfern Dev" },
    { hid: "og:type", property: "og:type", content: "website" },

    {
      hid: "og:title",
      property: "og:title",
     content:`${this.testimonialProfile.title}`,
    },
    {
      hid: "og:description",
      property: "og:description",
      content:`${this.testimonialProfile.title}`,
    },
    {
      hid: "og:image",
      property: "og:image",
      content:`${this.testimonialProfile.image}`,
    },
    { property: "og:image:width", content: "740" },
    { property: "og:image:height", content: "300" },


    { name: "twitter:card", content: "summary_large_image" },
    {
      hid: "twitter:url",
      name: "twitter:url",
      content: "https://bobross.com",
    },
    {
      hid: "twitter:title",
      name: "twitter:title",
      content:`${this.testimonialProfile.title}`,
    },
    {
      hid: "twitter:description",
      name: "twitter:description",
      content:`${this.testimonialProfile.title}`,
    },
    {
      hid: "twitter:image",
      name: "twitter:image",
      content:`${this.testimonialProfile.image}`,
    },
  ],

  }

},



    mounted() {

      if (window.innerWidth > 420) {
        this.isAviable = false
      } else {
         setTimeout(() => {
            this.isLoading = false

          }, 2000);
       /*  let {
          name,
          username,
          image,
          categoryColor,
          profession,
          redirecTo,
        } = this.$route.query

        if (username && name && image && categoryColor && profession && redirecTo) {
          console.log(image);
          setTimeout(() => {
            this.isLoading = false
            this.testimonialProfile = this.$route.query
          }, 2000);
        } else {
          this.$router.push('/')
        } */

      }
    },







  }

</script>


