<template>
  <div class="company">
    <div class="company__content">
      <div class="company__top">
        <div class="credentials">
          <span class="name">{{company_name}}</span>
          <div class="links">
            <ul>
              <li v-if="facebookUrl">
                <a :href="facebookUrl" class="links__facebook">
                  <i class="fa fa-facebook"></i>
                </a>
              </li>
              <li v-if="linkedInUrl">
                <a :href="linkedInUrl" class="links__linkedin">
                  <i class="fa fa-linkedin" aria-hidden="true"></i>
                </a>
              </li>
              <li v-if="twitterUrl">
                <a :href="twitterUrl" class="links__twitter">
                  <i class="fa fa-twitter" aria-hidden="true"></i>
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="company__description">
        <img :src="!errorLoading ? logo : alt" @error="imageLoadError" />
        <div class="company__description--text">
          <h3>{{title}}</h3>
          <p>{{isExpand ? Long_description : Short_description}}</p>
          <h4 v-if="isExpand">Areas of interest</h4>
          <ul class="specialisations" v-if="isExpand">
            <li v-for="spec of specialities" class="specialisation">{{spec}}</li>
          </ul>
          <a href="#" class="cta" @click="readMore">
            <span>{{isExpand ? 'Read More' : 'Show Less'}}</span>
          </a>
        </div>
      </div>
    </div>
    <div class="company__img">
      <a :href="website">
        <img :src="screenShot" alt="company Screenshot" />
      </a>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.company {
  width: 100%;
  max-width: 100rem;
  padding: 2rem 2rem;
  margin: 40px;
  background-color: #fff;
  box-shadow: 0 1.4rem 8rem rgba(0, 0, 0, 0.2);
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 0.8rem;

  @media screen and (max-width: 1068px) {
    max-width: 80rem;
    margin: 100px 1rem;
    padding: 2.5rem;
    flex-direction: column;
  }

  &__content {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  &__img {
    min-width: 50rem;
    max-width: 50rem;
    transform: translateX(8rem);
    height: 30rem;
    position: relative;

    @media screen and (max-width: 1200px) {
      min-width: 30rem;
      max-width: 30rem;
      transform: translateX(4rem);
    }

    @media screen and (max-width: 1080px) {
      min-width: 30%;
      max-width: 90%;
      height: 40rem;
      transform: translateY(8rem);
    }
    img {
      width: 100%;
      height: 100%;
      -o-object-fit: cover;
      object-fit: cover;
      display: block;
      border-radius: 0.8rem;
    }
  }

  &__top {
    width: 90%;
    align-self: start;
    padding-left: 0.4rem;
    margin-bottom: 1rem;

    @media screen and (max-width: 1080px) {
      width: 100%;
    }

    div.credentials {
      width: 90%;
      display: flex;
      align-items: center;
      justify-content: space-between;
      position: relative;

      @media screen and (max-width: 1060px) {
        align-items: center;
        justify-content: center;
        flex-direction: column;
        width: 100%;
      }
      .name {
        font-size: 2rem;
        display: block;
        margin: 0.5rem;
      }
      .links {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 30%;
        ul {
          padding: 0;
          margin: 0;
          display: flex;
          li {
            list-style: none;
            margin: 0 1rem;

            &:nth-child(1) a:hover {
              background-color: #3b5999;
            }

            &:nth-child(2) a:hover {
              background-color: #2867b2;
            }

            &:nth-child(3) a:hover {
              background-color: #55acee;
            }

            a {
              position: relative;
              display: block;
              width: 3.5rem;
              height: 3.5rem;
              border-radius: 50%;
              background-color: #fff;
              text-align: center;
              transition: 0.6s;
              box-shadow: 0 5px 4px rgba(0, 0, 0, 0.2);
              display: flex;
              align-items: center;
              justify-content: center;
              text-decoration: none;
              outline: none;

              &:hover {
                transform: translate(0, -5px);
                .fa {
                  color: #fff;
                }
              }
              .fa {
                font-size: 2rem;
                transition: 0.6s;
                color: #000;
              }
            }
          }
        }
      }
    }
  }

  &__description {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    width: 100%;

    @media screen and (max-width: 1060px) {
      margin-top: 2rem;
      padding-top: 2rem;
      flex-direction: column;
      align-items: center;
    }

    img {
      width: 10rem;
      height: 10rem;
      margin: 1rem;
    }
    &--text {
      margin-top: 1rem;
      margin-left: 2rem;

      @media screen and (max-width: 1080px) {
        margin-top: 0;
        margin-left: 0;
        text-align: center;
      }

      h3 {
        display: block;
        color: rgba(0, 0, 0, 0.5);
        font-size: 1.6rem;
        font-weight: 600;
        margin: 0 0 0.5rem 0;
      }

      p {
        margin-bottom: 1rem;
        font-size: 1.4rem;
        line-height: 2rem;
        color: #000;
      }

      h4 {
        font-size: 1.5rem;
        color: #999;
      }

      .specialisations {
        padding: 1.5rem;
        li {
          margin-bottom: 1rem;
          font-size: 1.4rem;
          color: #000;
        }
      }

      a {
        position: relative;
        display: inline-block;
        padding: 1.5rem 3rem;
        letter-spacing: 1px;
        text-transform: uppercase;
        font-size: 1.2rem;
        color: #fff;
        background-image: linear-gradient(to right, #4facfe 0%, #00f2fe 100%);
        border-radius: 0.8rem;
        outline: none;
        text-decoration: none;
        transition: all 0.2s;
        box-shadow: 2px 3px 5px rgba(0, 0, 0, 0.2);
        margin-top: 2rem;
        z-index: 1;

        span {
          position: relative;
          z-index: 11111;
        }

        &::after {
          content: "";
          display: flex;
          align-items: center;
          justify-content: center;
          width: 100%;
          height: 100%;
          position: absolute;
          top: 0;
          left: 0;
          background-image: linear-gradient(to right, #00f2fe 0%, #4facfe 100%);
          border-radius: 0.8rem;
          opacity: 0;
          transition: all 0.7s;
          z-index: 2;
        }

        &:hover {
          transform: scale(1.01);
          box-shadow: 3px 4px 7px rgba(0, 0, 0, 0.2);
        }

        &:hover::after {
          opacity: 0.7;
          transform: scale(1.01);
        }
      }
    }
  }
}
</style>
<script>
export default {
  data() {
    console.log(this.specialities);
    return {
      errorLoading: false,
      alt: "",
      isExpand: false
    };
  },
  props: {
    company_name: String,
    logo: String,
    email: String,
    title: String,
    rating: Number,
    screenShot: String,
    twitterUrl: String,
    linkedInUrl: String,
    facebookUrl: String,
    specialities: Array,
    companyAddress: String,
    Short_description: String,
    Long_description: String,
    website: String
  },
  methods: {
    imageLoadError() {
      this.errorLoading = true;
      this.alt =
        "https://toppng.com/uploads/preview/company-name-logo-11551052030ob9tu5iwdn.png";
    },
    readMore() {
      this.isExpand = !this.isExpand;
    }
  }
};
</script>