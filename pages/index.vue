<style type="text/css">
.clickable:hover {
  color: #5efc8d;
}
</style>
<template>
  <v-layout column justify-center align-center>
    <h2 class="headline pb-5">
      Share your Passport data
    </h2>
    <v-flex xs12 sm8 md6 d-flex class="pb-5 mb-5">
      <v-hover>
        <v-card
          slot-scope="{ hover }"
          :class="`text-xs-center elevation-${hover ? 10 : 2}`"
          extended
        >
          <template class="text-xs-center text-center">
            <v-btn
              fab
              absolute
              bottom
              class="clickable"
              style="left: 40%; right: 40%"
              @click="show = !show"
            >
              <v-icon class="clickable">
                mdi-{{ show ? 'arrow-up' : 'arrow-down' }}
              </v-icon>
            </v-btn>
          </template>
          <a :to="url">
            <v-icon
              :href="url"
              class="clickable pt-1 pl-6 pr-6 mt-4 ml-4 mr-4"
              size="248px"
            >
              mdi-telegram
            </v-icon>
          </a>
          <v-card-title
            class="text-xs-center pt-0 pb-4 mb-4 justify-center body-1"
          >
            What data is being shared?
          </v-card-title>
          <v-slide-y-transition>
            <v-list v-show="show" class="pt-0 pb-4 mb-4">
              <v-list-item>
                <v-list-item-icon>
                  <v-icon>mdi-contacts</v-icon>
                </v-list-item-icon>

                <v-list-item-title>Personal Details</v-list-item-title>
              </v-list-item>
              <v-list-item>
                <v-list-item-icon>
                  <v-icon>mdi-home</v-icon>
                </v-list-item-icon>

                <v-list-item-title>Residential Address</v-list-item-title>
              </v-list-item>

              <v-list-group
                prepend-icon="mdi-account-card-details"
                value="true"
                no-action
              >
                <template v-slot:activator>
                  <v-list-item-title>A valid ID (one of)</v-list-item-title>
                </template>

                <v-list-item v-for="(id, i) in ids" :key="i">
                  <v-list-item-title v-text="id"></v-list-item-title>
                </v-list-item>
              </v-list-group>

              <v-list-group
                prepend-icon="mdi-file-document"
                value="true"
                no-action
              >
                <template v-slot:activator>
                  <v-list-item-title
                    >Proof of address (one of)</v-list-item-title
                  >
                </template>

                <v-list-item v-for="(doc, i) in docs" :key="i">
                  <v-list-item-title v-text="doc"></v-list-item-title>
                </v-list-item>
              </v-list-group>
            </v-list>
          </v-slide-y-transition>
        </v-card>
      </v-hover>
    </v-flex>
    <v-btn outlined color="#5efc8d" :href="about">
      What is Telegram Passport?
    </v-btn>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      ids: ['Passport', 'Driver license', 'Identity card'],
      docs: ['Utility bill', 'Bank statement', 'Rental agreement'],
      show: false,
      contacts: 'memory',
      url:
        'tg://resolve?domain=telegrampassport&bot_id=901198298&scope=%7B%22v%22%3A%201%2C%20%22d%22%3A%20%5B%22pd%22%2C%20%22ad%22%2C%20%22em%22%2C%20%7B%22_%22%3A%20%5B%22passport%22%2C%20%22driver_license%22%2C%20%22identity_card%22%5D%7D%2C%20%7B%22_%22%3A%20%5B%22utility_bill%22%2C%20%22bank_statement%22%2C%20%22rental_agreement%22%5D%7D%5D%7D&public_key=-----BEGIN%20PUBLIC%20KEY-----%0AMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxFgESPAnVHvJCtxUnDEp%0A5KEqFJYstd08Wu0rNxXok1MsS6NUgxCtiPAqb%2By8Bt4qpGJmFEv%2Fo%2FZiTXILeD4a%0A%2BJJR1I2uYnZwXMAQ9weLhbwcjIJECciVINUEegg%2FHEsK9DBvHkrUZA2%2FMGvrU7sP%0A8oLuymOaUG5At2rTnhHuukINQO90dYhzHybIE6nsj3eDcpkxG5ExTUw%2F2BwITucT%0AFsxPbjEf%2Bw2DH%2F%2FEFXK9YMXJ7MLOPd%2BJN01LlGqqknVPPyE7CrrreX1Cn7Y2slOK%0AyT9iwY%2FZWsJCR74l8CsEzmeVFQp2%2FLr4XLocY6f0fQ18843bvM089OQKmUILhGTb%0ASwIDAQAB%0A-----END%20PUBLIC%20KEY-----%0A&nonce=0b462081738dee13&callback_url=tg%3A//resolve%3Fdomain%3Dkycdemo_bot&payload=nonce',
      about: 'https://telegram.org/blog/passport'
    }
  }
}
</script>
