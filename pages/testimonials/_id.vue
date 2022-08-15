<template>
  <section class="testimonial-section d-flex justify-center align-center">
    <h2>Create project d fffdd</h2>
   <li class="profile-info-item profile-info-item--name font-weight-bold">{{ fetchedData.title }}</li>
   lo
  </section>
</template>
<script>
import getSiteMeta from '../../utils/getHead'
  export default {
      computed: {
  meta() {
    const metaData = {
      type: "article",
      title: this.testimonialProfileData.title,
      description: this.testimonialProfileData.description,
      url: `${this.$config.baseUrl}/testimonials/${this.$route.params.slug}`,
      mainImage: this.testimonialProfileData.image,
    };
    return getSiteMeta(metaData);
  }
},

    data() {
      return {
        isAviable: true,
        isLoading: true,
        testimonialProfileData:{
          title:'this a new title',
         image:'https://cdn.pixabay.com/photo/2021/08/25/07/21/cat-6572630__340.jpg',
         description:'lorepm ipsum'

        }
        /* testimonialProfile: {} */
      }
    },
     /*  async asyncData({query,redirect,store,params}) {
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

          }else{
               redirect('/')
          }

        } catch (error) {
         redirect('/')
        }




      return { testimonialProfile }
    },
 */
async  asyncData(context) {
    return context.$axios
      .get('https://jsonplaceholder.typicode.com/posts/1')
      .then((res) => {
        return { fetchedData: res.data }
      })
  },
head() {
  return {
    title: this.testimonialProfileData.title,
    meta: [
      ...this.meta,



      { name: "twitter:label1", content: "Written by" },
      { name: "twitter:data1", content: "Bob Ross" },
      { name: "twitter:label2", content: "Filed under" },

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


