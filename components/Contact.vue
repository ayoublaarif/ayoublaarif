<template>
    <div id="contact" class="me-contact" data-scroll-section>
        <div class="container">
            <div class="contact">
            <div class="contact_content">

            
                <div class="face"><img src="@/assets/svg/face.svg" class="face-svg"/></div>
                <div class="title">
                    <p> Let's create something <br> interesting. </p>
                </div>
                <div class="contact_items">
                    <div class="email con">
                        <p> Business Mail </p>
                        <a href="mailto:me@ayoublaarif.com"> me@ayoublaarif.com </a>
                        <div class="email_line"></div>
                    </div>
                    <div class="phone con">
                        <p> Phone Number </p>
                        <a href="mailto:me@ayoublaarif.com"> +212 06 1553 9198 </a>
                        <div class="phone_line"></div>
                    </div>
                    <div class="media con">
                        <p> Social Media </p>
                        <a href="mailto:me@ayoublaarif.com"> +212 06 1553 9198 </a>
                        <div class="phone_line"></div>
                    </div>
                </div>
                </div>
            </div>
            <div class="footer">
                    <div class="footer_line"></div>
                    <div class="footer_content">
                        <p>Developed by Ayoub Laarif</p>
                        <p>© 2020 all rights reserved</p>
                    </div>
                    
                </div>
        </div>
    </div>
</template>

<script>
export default {

data(){
    return{
        lmD: null,
    }
},

  mounted() {

  },
  destroyed(){
  }
}
</script>

<style lang="scss" scoped>

    .me-contact{
        grid-area: contact;
        width: 80vw;
        min-height: 100vmin;
        color: #000;
        

        .container{
            
            //border: red 2px solid;
            margin: 0 auto;
            height: 100%;
            display: grid;
            grid-template-rows: 80% 20%;

            .contact{
                
                
                //border: black 2px solid;
                display: flex;
                //top: 10%;
                justify-content: center;
                align-items: center !important;
            
                //display: flex;
                text-align: center;

            .contact_content{
                //position: relative;
                margin: auto 0;


                //border: blue 2px solid;
                .face{
                    position: relative;
                    width: 6rem;
                    margin: 0 auto;
                    .face-svg{
                        width: 100%;
                    }
                    
                }
                
                .title{
                    @include ivymode(2.8rem,1rem,400);
                    margin: 1.4rem 0;
                    //color: #ffffff;

                }

                .contact_items{

                    display: grid;
                    grid-template-rows: auto auto auto;
                    justify-content: center;
                    
                    .con{
                        display: grid;
                        grid-template-rows: 1.4rem auto;
                        margin: 0.6rem 0;
                        align-items: center;
                        cursor: pointer;
                        p{
                            @include montserrat(0.6rem,-0.4rem,500);
                            text-transform: uppercase;
                            opacity: 0.24;
                            //border: black 2px solid;
                        }
                        a{
                            @include montserrat(0.8rem,-0.4rem,500);
                            text-transform: uppercase;
                            color: #000;//$trdColor;
                            text-decoration: none;
                        }
                    }
                    .email{
                    }
                    .phone{

                    }
                    .media{

                    }

                }

            }

                

                

                
               
                

                


                /*.email{
                    //@include montserrat(5rem,1rem,500);
                    

                    
                    
                    
                    .email_line{
                        width: 0%;
                        height: 0.2rem;
                        background-color: #000;
                        margin-top: -0.6rem;
                    }
                    &:hover{
                        .email_line{
                            width: 100%;
                            transition: width 0.3s ease-out;
                        }
                    }
                }

                .phone{
                    //@include montserrat(5rem,1rem,500);
                    
                    .phone_line{
                        width: 0%;
                        height: 0.2rem;
                        background-color: #000;
                        margin-top: -0.6rem;
                    }


                }*/



            }

            .footer{
                    
                        margin-top: 2rem;
                        .footer_line{
                            width: 80vw;
                            height: 0.1rem;
                            background-color: #000;
                        }
                        .footer_content{
                            //
                            @include montserrat(0.8rem,0rem,500);
                            text-transform: uppercase;
                            width: 100%;
                            display: flex;
                            justify-content: space-between;
                            margin-top: 2rem;
                        }
                    }

            

        }
    }


</style>
