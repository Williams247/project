<template>
  <div class="flex" id="container">
    <div class="left-pane">
      <div id="move-to-left">
        <SideMenu :links="links" />
      </div>
    </div>
    <div class="right-pane container pt-3 pb-6">
      <div id="mobile-menu" @click="showMobileMenu">
        <i class="fa fa-bars"></i>
      </div>
      <NavBar
        :handleSearchImage="handleSearchImage"
        :loader="loader"
      />
      <Menu />
      <div class="flex flex-wrap" id="card-main-container">
        <div
          v-for="(item, index) in imageData"
          :key="index"
          id="card-info-container"
        >
          <Card
            :image="item.largeImageURL"
            :tags="item.tags"
            :user="item.user"
          />
        </div>
      </div>
    </div>
    <div
      :style="[open ? {marginLeft: '0'} : {marginLeft: '-150%'}]"
      id="mobile-menu-container"
    >
    <MobileMenu
      :open="open"
      :showMobileMenu="showMobileMenu"
    >
      <SideMenu :links="links" />
    </MobileMenu>
    </div>
    <Modal
      :message="modalMessage"
      :isModal="isModal"
      :handleOpenCloseModal="handleOpenCloseModal"
    />
    <Loader :loading="bigLoader" />
  </div>
</template>

<script>
import Axios from "axios";
import NavBar from "../components/NavBar";
import SideMenu from "../components/SideBar";
import Menu from "../components/Menu";
import Card from "../components/Card";
import Modal from "../components/Modal";
import Loader from "../components/Loader";
import MobileMenu from "../components/MobileMenu";
import sampleLinks from "../constants/sample-links.json";

export default {
  name: "Layout",
  components: {
    NavBar,
    SideMenu,
    Menu,
    Card,
    Modal,
    Loader,
    MobileMenu
  },
  data() {
    return {
      imageData: [],
      links: sampleLinks[0],
      modalMessage: "",
      isModal: false,
      bigLoader: true,
      loader: false,
      open: false
    };
  },
  methods: {
     showMobileMenu() {
      this.open = !this.open
    },
    handleOpenCloseModal() {
      // Modal control
      this.modalMessage = "";
      this.isModal = false;
    },
    async handleGetRandomPhotos () {
      // @GET
      // Functionality to get random image for a user if local store is empty
      const unsplashApiKey = "21875002-1ad64de0d03b15dae54da65fa&q";
      try {
        const { data: { hits } } = await Axios.get(`https://pixabay.com/api/?key=${unsplashApiKey}=${'meat pie'}&image_type=photo`);
        console.log(hits);
        this.imageData = hits;
        this.bigLoader = false
      } catch (error) {
        this.modalMessage = "Failed to fetch results, please try again!";
        this.isModal = true;
        console.log(error);
        this.bigLoader = false;
      }
    },
    async handleSearchImage(event) {
      // @GET
      // Functionality to get a specific image for a user
      const imageSearch = event.target.search_term.value;
      const unsplashApiKey = "21875002-1ad64de0d03b15dae54da65fa&q";

      if (!imageSearch) {
        this.modalMessage = "Please enter a search word, i.e meat pie, milk....";
        this.isModal = true;
        return false;
      }

      this.imageData = [];

      this.loader = true;

      try {
        const {
          data: { hits },
        } = await Axios.get(
          `https://pixabay.com/api/?key=${unsplashApiKey}=${imageSearch.toLocaleLowerCase()}&image_type=photo`
        );

        console.log(hits);
        this.imageData = hits;

        this.modalMessage = "";
        this.isModal = false;
        this.loader = false;

      } catch (error) {
        this.modalMessage = "Failed to fetch results, please try again!";
        this.isModal = true;
        console.log(error);
        
        this.modalMessage = "";
        this.isModal = false;
        this.loader = false;
      }
    }
  },
  mounted() {
    this.handleGetRandomPhotos()
  }
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";

#container {
  min-height: 100vh;
  #mobile-menu-container {
   position: fixed;
   z-index: 333;
   bottom: 0;
   width: 100%;
   height: 100%;
   background: $light;
   padding-left: 68px;
   transition: 1s ease;
 }
  #mobile-menu {
    display: block;
    color: $grayed;
    border: 1px solid $grayed;
    width: 23px;
    display: flex;
    justify-content: center;
    margin-bottom: 23px;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 3px;
    padding-right: 3px;
    border-radius: $rounded;
    @media (min-width: 780px) {
      display: none;
    }
  }
  .left-pane {
    width: 19%;
    display: none;
    border-right: 1px solid $grayed;
    #move-to-left {
      margin-left: 22%;
    }
    @media (min-width: 780px) {
      display: block;
    }
  }
  .right-pane {
    width: 100%;
    @media (min-width: 780px) {
      width: 81%
    }
    #card-main-container {
      margin-left: -23px;
      #card-info-container {
        margin-top: 28px;
      }
    }
  }
}
</style>
