<script lang="ts">
export default {
  data() {
    return {
      layoutDesktop: "2x1",
      layoutMobile: "2x1",
      enableHoverCTA: false,
      enableHoverWithArrowIcon: false,
      positioningDesktop: "alignLeft alignCenter",
      positioningMobile: "alignLeft alignTop",
      frontSide: {
        title: {
          title: "Lorem Ipsum Dolor sit amet",
          titleBackgroundColorDesktop: "#000",
          titleBackgroundColorTablet: " #000",
          titleBackgroundColorMobile: "#000",
          titleFontSizeDesktop: "24",
          titleFontSizeTablet: "24",
          titleFontSizeMobile: "16",
        },
        headerTag: "h3",
        description: {
          description:
            "Sorade neroskap. Mävis revis. Änis hexaheten. Bovis nil. Intranat aheten. Ratt nesk. Rugt oktig. Hemir eneras. Bev sedat.",
          descriptionBackgroundColorDesktop: "#000",
          descriptionBackgroundColorTablet: "#000",
          descriptionBackgroundColorMobile: "#000",
          descriptionFontSizeDesktop: "14",
          descriptionFontSizeTablet: "14",
          descriptionFontSizeMobile: "14",
          descriptionLineHeightDesktop: "18",
          descriptionLineHeightTablet: "18",
          descriptionLineHeightMobile: "18",
        },
        cta1: {
          type: "categoryPicker",
          url: "",
          label: "CTA 1",
          colorFontDesktop: "#000",
          colorFontTablet: "#000",
          colorFontMobile: "#000",
        },
        cta2: {
          type: "categoryPicker",
          url: "",
          label: "CTA 2",
          colorFontDesktop: "#000",
          colorFontTablet: "#000",
          colorFontMobile: "#000",
        },
        mediaType: {
          image: {
            imageDesktop: "more_img.png",
            imageTablet: "/clientlib-resources/images/product-img-2x2.jpg",
            imageMobile: "/clientlib-resources/images/product-img-2x2.jpg",
            altTextImage: "alt editorial",
          },
          background: {
            bgColorDesktop: " ",
            bgColorTablet: " ",
            bgColorMobile: " ",
          },
          type: "image",
        },
      },
      backSide: {
        enableBackSide: false,
        title: {
          title: "Lorem Ipsum Dolor sit amet",
          titleBackgroundColorDesktop: "#fff",
          titleBackgroundColorTablet: "#fff",
          titleBackgroundColorMobile: "#fff",
          titleFontSizeDesktop: "24",
          titleFontSizeTablet: "24",
          titleFontSizeMobile: "15",
        },
        headerTag: "h2",
        description: {
          description:
            "Sorade neroskap. Mävis revis. Änis hexaheten. Bovis nil. Intranat aheten. Ratt nesk. Rugt oktig. Hemir eneras. Bev sedat.",
          descriptionBackgroundColorDesktop: "#fff",
          descriptionBackgroundColorTablet: "#fff",
          descriptionBackgroundColorMobile: "#fff",
          descriptionFontSizeDesktop: "14",
          descriptionFontSizeTablet: "14",
          descriptionFontSizeMobile: "14",
          descriptionLineHeightDesktop: "18",
          descriptionLineHeightTablet: "18",
          descriptionLineHeightMobile: "18",
        },
        backgroundColorDesktopBackSide: "#4E555A",
        backgroundColorTabletBackSide: "#4E555A",
        backgroundColorMobileBackSide: "#4E555A",
        cta1: {
          url: "",
          label: "CTA 1",
          colorFontDesktop: "#fff",
          colorFontTablet: "#fff",
          colorFontMobile: "#fff",
        },
        cta2: {
          url: "",
          label: "CTA 2",
          colorFontDesktop: "#fff",
          colorFontTablet: "#fff",
          colorFontMobile: "#fff",
        },
      },
    };
  },
  computed: {
    getDescriptionPosition() {
      switch (this.positioningDesktop) {
        case "alignLeft alignTop":
          return {
            top: "20px",
            left: "20px",
          };
        case "alignLeft alignBottom":
          return {
            bottom: "20px",
            left: "20px",
          };
        case "alignLeft alignCenter":
          return {
            top: "50%",
            left: "20px",
            transform: "translateY(-50%)",
          };
        case "alignCenter alignTop":
          return {
            top: "20px",
            left: "50%",
            transform: "translateX(-50%)",
          };
        case "alignRight alignTop":
          return {
            top: "20px",
            right: "20px",
          };
        case "alignRight alignBottom":
          return {
            bottom: "20px",
            right: "20px",
          };
        case "alignRight alignCenter":
          return {
            top: "50%",
            right: "20px",
            transform: "translateY(-50%)",
          };
        case "alignCenter alignCenter":
          return {
            top: "50%",
            left: "50%",
            transform: "translate(-50%, -50%)",
          };
        case "alignCenter alignBottom":
          return {
            bottom: "20px",
            right: "50%",
            transform: "translateX(50%)",
          };
        default:
          return {
            top: "20px",
            left: "20px",
          };
      }
    },
  },
};
</script>

<template>
  <div
    class="main_wrapper"
    :style="{
      backgroundImage: `url(${
        './assets/images/' + frontSide.mediaType.image.imageDesktop
      })`,
    }"
  >
    <img
      :src="`${'./assets/images/' + frontSide.mediaType.image.imageDesktop}`"
      :style="{ visibility: 'hidden' }"
    />
    <div
      :style="{
        position: 'absolute',
        ...getDescriptionPosition,
      }"
      class="text-2xl"
    >
      {{ frontSide.title.title }}
      <div class="w-1/2 mt-4 text-sm">
        {{ frontSide.description.description }}
      </div>
      <div class="flex flex-row gap-6 mt-5">
        <div class="text-sm font-medium underline">
          {{ frontSide.cta1.label }}
        </div>
        <div class="text-sm font-medium underline">
          {{ frontSide.cta2.label }}
        </div>
      </div>
    </div>
    <img src="/assets/icons/Union.svg" />
  </div>
</template>

<style scoped>
.main_wrapper {
  position: relative;
  background-repeat: no-repeat;
  background-size: contain;
  width: fit-content;
}
.description {
  position: absolute;
}
</style>
