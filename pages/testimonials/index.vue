<template>
  <section class="testimonial-section d-flex justify-center align-center">
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
      async asyncData({query,redirect,store}) {
      let testimonialProfile = {}
      let {
          id
        } = query


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
 head() {
  return {
    title: `${this.testimonialProfile.title}-web`,
    meta: [
       /*  {
        hid: "description",
        name:  'description',
        content: `${this.testimonialProfile.user.fullName}`,
      },
        {
           hid: 'og:title',
        property:  'og:title',
        content:  `${this.testimonial.user.fullName}-user`,
      },
      {
        hid: "og:description",
        property:  'og:description',
        content: `${this.testimonialProfile.user.fullName}`,
      },
      {
         hid: 'og:image',
        property:  'og:image',
        content: `${this.testimonialProfile.user.image}`
      },
      //twitter
   {
        hid: "twitter:title",
        name: "twitter:title",
        content: this.testimonialProfile.user.fullName,
      },
      {
        hid: "twitter:description",
        name: "twitter:description",
        content: this.testimonialProfile.user.fullName,
      },
      {
        hid: "twitter:image",
        name: "twitter:image",
        content:`${this.testimonialProfile.user.image}`,
      }, */

    /*  {
        hid: "description",
        name: "description",
        content: this.testimonialProfile.user.fullName,
      },
      {
        hid: "og:title",
        name: "og:title",
        content: this.testimonialProfile.user.fullName,
      },
      {
        hid: "og:description",
        name: "og:description",
        content: this.testimonialProfile.user.fullName,
      },
      {
        hid: "og:type",
        property: "og:type",
        content: "website",
      },


      {
        hid: "twitter:title",
        name: "twitter:title",
        content: this.testimonialProfile.user.fullName,
      },
      {
        hid: "twitter:description",
        name: "twitter:description",
        content:this.testimonialProfile.user.fullName,
      },
      {
        hid: "twitter:image",
        name: "twitter:image",
        content:this.testimonialProfile.user.image,
      },
      {
        hid: "og:image",
        property: "og:image",
        content: this.testimonialProfile.user.image,
      },
 */

          {
                hid: 'description',
                name: 'description',
                content: this.testimonialProfile.title,
            },
            {
                hid: 'apple-mobile-web-app-title',
                name: 'apple-mobile-web-app-title',
                content: this.testimonialProfile.title,
            },
            {
                hid: 'og:title',
                name: 'og:title',
                content:  this.testimonialProfile.title,
            },
            {
                hid: 'og:image',
                property: 'og:image',
                content: `${this.testimonialProfile.image}`,
            },
            {
                hid: 'og:description',
                property: 'og:description',
                content:this.testimonialProfile.title,
            },





    ],

  };
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


