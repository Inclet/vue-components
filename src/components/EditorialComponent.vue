<script lang="ts">
export default {
  data() {
    return {
      layoutDesktop: "2x1",
      layoutMobile: "2x1",
      enableHoverCTA: false,
      enableHoverWithArrowIcon: false,
      positioningDesktop: "alignLeft alignBottom",
      positioningMobile: "alignLeft alignTop",
      frontSide: {
        title: {
          title: "Lorem Ipsum Dolor sit am",
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
          label: "CTA1",
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
            imageDesktop: "shoe_img.png",
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
          label: "CTA MAIN",
          colorFontDesktop: "#fff",
          colorFontTablet: "#fff",
          colorFontMobile: "#fff",
        },
        cta2: {
          url: "",
          label: "CTA MAIN",
          colorFontDesktop: "#fff",
          colorFontTablet: "#fff",
          colorFontMobile: "#fff",
        },
      },
      isShowBackside: false,
      isHover: false,
    };
  },
  computed: {
    getDescriptionPosition() {
      // Check device
      const positionDevice = this.isMobile()
        ? this.positioningMobile
        : this.positioningDesktop;

      switch (positionDevice) {
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
    // getTitleColor() {
    //   let color = "";
    //   switch (document.getScreen) {
    //     case "Mobile":
    //       color = this.frontSide.title.titleBackgroundColorMobile;
    //       break;
    //     default:
    //       color = "#000";
    //       break;
    //   }
    //   return {
    //     color,
    //   };
    // },
  },
  methods: {
    handleShowBackside() {
      this.isShowBackside = !this.isShowBackside;
    },
    isMobile(): boolean {
      return window.matchMedia("(max-width: 767px)").matches;
    },
    getValue() {
      return this.isMobile() ? "16px" : "20px";
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
      <div class="flex cursor-pointer">
        <img src="/assets/icons/left-arrow.svg" v-if="isHover" class="pr-3" />
        <div
          class="text-2xl font-bold"
          @mouseover="isHover = true"
          @mouseleave="isHover = false"
        >
          {{ frontSide.title.title }}
        </div>
      </div>
      <div
        class="w-1/2 mt-4 text-sm description-test"
        :style="{
          '--description-color': `${frontSide.title.titleBackgroundColorDesktop}`,
          '--description-mobile-color': `${frontSide.title.titleBackgroundColorDesktop}`,
        }"
      >
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
      <img
        src="/assets/icons/Union.svg"
        color="#000000"
        class="absolute bottom-0 right-8 cursor-pointer"
        @click="handleShowBackside"
      />
    </div>
    <div
      v-if="isShowBackside"
      class="absolute top-0 left-0 bg-black text-white p-5 h-full w-full"
    >
      <div class="text-2xl font-bold">{{ backSide.title.title }}</div>
      <div class="w-1/2 mt-4 text-sm font-normal">
        {{ backSide.description.description }}
      </div>
      <div class="flex flex-row gap-6 mt-5">
        <div class="text-sm font-medium underline">
          {{ backSide.cta1.label }}
        </div>
        <div class="text-sm font-medium underline">
          {{ backSide.cta2.label }}
        </div>
      </div>
      <div
        class="absolute bottom-5 right-6 cursor-pointer p-2"
        @click="handleShowBackside"
      >
        <img src="/assets/icons/remove.svg" />
      </div>
    </div>
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

.description-test {
  color: var(--description-color);
}

/* smartphones, iPhone, portrait 480x320 phones */
@media only screen and (min-device-width: 320px) and (max-device-width: 768px) {
  .description-test {
  color: var(--description-color);
}
}
</style>
