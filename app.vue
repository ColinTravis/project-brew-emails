<script setup>
import { EButton, EFont, ETailwind } from 'vue-email'
const tailwindConfig = {
  theme: {
    fontFamily: {
      sans: ['Fredoka', 'Times New Roman'],
    },
    extend: {
      colors: {
        transparent: 'transparent',
        current: 'currentColor',
        black: '#31312D',
        'dark-gray': '#c9c7c7',
        purple: '#623CEA',
        cream: '#FAF4E6',
        white: '#FFFFFF',
        yellow: '#EFAD06',
        blue: '#60B2E5',
        'light-gray': '#D9D9D9',
        red: '#ED1C24'
      },
      borderWidth: {
        3: '3px'
      },
      borderRadius: {
        standard: '13px'
      },

    },
  },
}

const props = defineProps({
  userFirstName: {
    type: String,
    default: 'Test',
  },
  loginDevice: {
    type: String,
    default: 'Chrome on Mac OS X',
  },
  loginLocation: {
    type: String,
    default: 'Upland, California, United States',
  },
  loginIp: {
    type: String,
    default: '47.149.53.167',
  },
  loginDate: {
    type: Date,
    default: new Date('September 7, 2022, 10:58 am'),
  },
})

const formattedDate = new Intl.DateTimeFormat('en', {
  dateStyle: 'long',
  timeStyle: 'short',
}).format(props.loginDate)

const paragraph = {
  fontSize: '16px',
}

const logo = {
  padding: '30px 20px',
}

const button = {
  border: '3px solid #31312D',
}

const content = {
  border: '1px solid rgb(0,0,0, 0.1)',
  borderRadius: '3px',
  overflow: 'hidden',
}

const boxInfos = {
  padding: '20px 40px',
}

const containerImageFooter = {
  padding: '45px 0 0 0',
}
</script>

<template>
  <EHtml>
    <EHead>
      <EFont font-family="Fredoka" :web-font="{
        url: 'https://fonts.gstatic.com/s/fredoka/v14/X7nP4b87HvSqjb_WIi2yDCRwoQ_k7367_B-i2yQag0-mac3O8SL8EemKttxNbikt.woff2',
        format: 'woff2',
      }" font-weight="400" font-style="normal" />
      </EHead>
      <EPreview>Yelp recent login</EPreview>
      <ETailwind :config="tailwindConfig">
      <EBody class="bg-cream">
        <EContainer>
          <ESection :style="logo">
            <EImg src="/static/yelp-logo.png" />
          </ESection>

          <ESection class="py-3 px-10 border-3 border-black rounded-standard bg-light-gray" :style="content">
            <EImg width="200" class="mx-auto" src="https://res.cloudinary.com/project-brew/image/upload/v1707202627/brewster/email/Brewster-logo_j9j6it.png" />

            <ERow :style="{
              ...boxInfos,
              paddingBottom: 0,
            }">
              <EColumn>
                <EHeading style="font-size: 32; font-weight: bold; text-align: center"> Hi {{ userFirstName }},
                </EHeading>
                <EHeading :style=fontTest class="text-center text-2xl" as="h2">
                  You've been invited.
                </EHeading>

                <!-- <EText :style="paragraph">
                  <b>Time: </b>
                  {{ formattedDate }}
                </EText>
                <EText :style="{ ...paragraph, marginTop: '-5px' }">
                  <b>Device: </b>
                  {{ loginDevice }}
                </EText>
                <EText :style="{ ...paragraph, marginTop: '-5px' }">
                  <b>Location: </b>
                  {{ loginLocation }}
                </EText>
                <EText :style="{
                  color: 'rgb(0,0,0, 0.5)',
                  fontSize: 14,
                  marginTop: '-5px',
                }">
                  *Approximate geographic location based on IP address: {loginIp}
                </EText>

                <EText class="text-black font-fredoka text-lg"> If this was you, there's
                  nothing else you need to do.
                </EText>
                <EText :style="{ ...paragraph, marginTop: '-5px' }"> If this wasn't you or if you have additional
                  questions,
                  please see our support page. </EText> -->
              </EColumn>
            </ERow>
            <ERow :style="{ ...boxInfos, paddingTop: '0' }">
              <EColumn class="flex justify-center w-full" col-span="{2}">
                <EButton :style="button" href="#"
                  class="rounded-standard border-3 border-black bg-yellow text-2xl px-6 py-1 block text-white hover:bg-blue">
                  Button </EButton>
              </EColumn>
            </ERow>
          </ESection>

          <ESection :style="containerImageFooter">
            <EImg width="620" src="/static/yelp-footer.png" />
          </ESection>

          <EText :style="{
            textAlign: 'center',
            fontSize: 12,
            color: 'rgb(0,0,0, 0.7)',
          }">
            © 2022 | Yelp Inc., 350 Mission Street, San Francisco, CA 94105, U.S.A. | www.yelp.com
          </EText>
        </EContainer>
      </EBody>
    </ETailwind>
    </EHtml>
</template>
