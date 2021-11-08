<template>
  <div class="flex flex-direction-row-column" id="nav">
    <div class="left-pane">
      <div class="spacer" id="search-field-container">
        <div class="container">
          <form @submit.prevent="handleSearchImage">
            <div class="flex">
              <div id="search-icon-container">
                <div><i class="fa fa-search"></i></div>
              </div>
              <div id="search-input-container">
                <input
                  type="text"
                  class="pb-1"
                  name="search_term"
                  placeholder="Find Something..."
                />
              </div>
              <div id="button-container">
                <Button label="Search" :loading="loader" />
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
    <div class="right-pane">
      <div class="ml-1 flex">
        <div id="pane-1">
          <div id="bell">
            <span><i class="fa fa-bell"></i></span>
            <div id="notification">
              <span>3</span>
            </div>
            <div id="drop-down">
              <DropDown />
            </div>
          </div>
        </div>
        <div id="pane-2">
          <div class="mt-1">
            <img src="../assets/lady.jpg" alt="lady" id="lady" />
            <div id="online"></div>
          </div>
        </div>
        <div class="flex" id="pane-3">
          <div id="name">Abigail</div>
          <div id="arrow-down-icon">
            <span class="fa fa-chevron-down"></span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "./Button";
import DropDown from "./DropDown";
export default {
  name: "NavBar",
  props: {
    handleSearchImage: Function,
    loader: Boolean,
  },
  components: {
    Button,
    DropDown,
  },
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";
#nav {
  .spacer {
    padding-top: 14px;
    padding-bottom: 9px;
  }
  .left-pane {
    width: 100%;
    @media (min-width: 780px) {
      width: 75%;
    }
    #search-field-container {
      box-shadow: 0 0 18px#e1e1e4;
      width: 100%;
      border-radius: $rounded;
      #search-icon-container {
        width: 6%;
        color: $grayed-doubled;
        display: none;
        div {
          font-size: 22px;
          margin-top: -4px;
        }
        @media (min-width: 780px) {
          // Desktop size for search icon container
          display: block;
        }
      }
      #search-input-container {
        width: 74%;
        input {
          width: 95%;
          border: none;
          outline: none;
          color: $grayed-doubled;
        }
        @media (min-width: 780px) {
          // Desktop size for search field container
          width: 85%;
        }
      }

      #button-container {
        width: 10%;
      }
    }
  }
  .right-pane {
    width: 25%;
    margin-top: 12px;
    @media (min-width: 780px) {
      margin-top: 0;
      width: 25%;
    }
    #pane-1 {
      width: 50%;
      @media (min-width: 780px) {
        width: 25%;
      }
      #bell {
        margin-top: 8px;
        color: $primary;
        margin-left: 12px;
        font-size: 25px;
        &:hover {
          #drop-down {
            display: block;
          }
        }
        #drop-down {
          background: $light;
          width: 230px;
          margin-left: -50px;
          margin-top: 23px;
          position: absolute;
          display: none;
          box-shadow: 0 0 18px#e1e1e4;
          z-index: 15;
          &:after {
            content: "";
            position: absolute;
            bottom: 100%;
            left: 50%;
            margin-left: -60px;
            border-width: 9px;
            border-style: solid;
            border-color: transparent transparent $light transparent;
          }
        }
      }
      #notification {
        position: absolute;
        background: $danger;
        border-radius: $absolutely-round;
        width: 12px;
        height: 12px;
        font-size: 9px;
        color: $light;
        font-weight: bold;
        text-align: center;
        margin-top: -15px;
        margin-left: 13px;
      }
    }
    #pane-2 {
      width: 100%;
      @media (min-width: 780px) {
        width: 33%;
      }
      #lady {
        width: 40px;
        height: 40px;
        border-radius: $absolutely-round;
        margin-left: 23px;
      }
      #online {
        background: #35d261;
        width: 10px;
        height: 10px;
        border-radius: $absolutely-round;
        margin-top: -14px;
        margin-left: 52px;
        position: absolute;
        border: 1px solid $light;
      }
    }
    #pane-3 {
      width: 20%;
      margin-left: 23px;
      @media (min-width: 780px) {
        margin-left: 0;
      }
      color: $primary;
      #name {
        color: $primary;
        font-size: 14px;
        margin-top: 12px;
      }
      #arrow-down-icon {
        margin-top: 15px;
        margin-left: 13px;
        font-size: 9px;
      }
    }
  }
}
</style>
