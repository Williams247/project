<template>
  <div>
    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <FrontImage :image="image" :imgAlt="tags" />
          <div class="flip-card-major-content">
            <div class="flip-front-card-major-content-details">
              <div>{{ user.length > 10 ? `${user.slice(-6)}...` : user }}</div>
              <div>{{ tags.length > 30 ? `${tags.slice(-8)}...` : tags }}</div>
            </div>
          </div>
        </div>
        <div class="flip-card-back">
          <BackImage :image="image" :imgAlt="tags" />
          <div class="flip-back-card-major-content-details">
            <div>{{ user.length > 10 ? `${user.slice(-6)}...` : user }}</div>
            <div>{{ tags.length > 30 ? `${tags.slice(-8)}....` : tags }}</div>
          </div>
          <div class="flex pl-3">
            <div class="mt-2">
              <FlatButton icon="fa fa-heart-o" variant="danger" />
            </div>
            <div class="mt-2 left">
              <FlatButton icon="fa fa-thumbs-o-down" variant="primary" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FrontImage from "./FrontImage";
import BackImage from "./BackImage";
import FlatButton from "./FlatButton";
export default {
  name: "Card",
  props: {
    image: String,
    tags: String,
    user: String,
  },
  components: {
    FlatButton,
    FrontImage,
    BackImage,
  },
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";

.flip-card {
  background-color: transparent;
  width: 360px;
  height: $card-height;
  perspective: 1000px;
  cursor: pointer;
  border-radius: $rounded;
  margin-left: 24px;
  @media (min-width: 768px) {
    width: 340px;
  }
  @media (min-width: 780px) {
    width: 230px;
  }
  &:hover {
    .flip-card-inner {
      transform: rotateY(180deg);
    }
  }
  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  }
  .flip-card-front,
  .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    border-radius: $rounded;
    .flip-front-card-major-content-details {
      margin-top: 230px;
      color: $light;
      text-align: left;
      padding-left: 33px;
      div {
        &:first-child {
          font-size: 24px;
          font-weight: bold;
        }
      }
    }
    .flip-card-major-content {
      position: absolute;
      bottom: 0;
      background-image: linear-gradient(
        to top,
        rgba(0, 0, 0, 0.8),
        rgba(0, 0, 0, 0)
      );
      width: 100%;
      height: $card-height;
      border-radius: $rounded;
    }
  }

  .flip-card-front {
    background-color: #bbb;
    color: black;
  }

  .flip-card-back {
    background-color: $light;
    color: white;
    transform: rotateY(-180deg);
    .flip-back-card-major-content-details {
      text-align: left;
      padding-left: 17px;
      div {
        &:first-child {
          color: $primary;
          font-size: 24px;
          font-weight: bold;
        }
        &:last-child {
          color: $primary;
          font-size: 13.5px;
        }
      }
    }
  }
  .left {
    margin-left: 10px;
  }
}
</style>
