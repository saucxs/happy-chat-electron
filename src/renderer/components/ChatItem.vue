<template>
    <div class="chat-item">
        <div v-if="!me" class="otherchat">
          <svg class="icon img" aria-hidden="true" @click="lookInfo">
            <use xlink:href="#iconrobot"></use>
          </svg>
          <div class="nt"><span v-if="name">{{name}}</span><span v-if="time">{{time}}</span></div>
          <div class="msg">{{msg}}</div>
        </div>

        <div v-if="me" class="mychat">
          <svg class="icon img" aria-hidden="true" @click="lookInfo">
            <use xlink:href="#iconniu"></use>
          </svg>
          <div class="nt"><span v-if="time">{{time}}</span><span v-if="name">{{name}}</span></div>
          <div class="msg">{{msg}}</div>
        </div>


    </div>
</template>

<script>
    export default {
      name: 'chat-item',
      props: ['me', 'name', 'img', 'msg', 'time', 'href'],
      components: {},
      data () {
        return {}
    },

      computed: {},

      watch: {},

      methods: {
        lookInfo () {
          if (this.href) {
            this.$router.push(`/user_info/${this.href}`)
          } else {
            window.location.href = 'https:// github.com/saucxs/happy-chat-web'
          }
        }
      }
    }
</script>

<style lang="scss" scoped>
    .chat-item {
        width: 100%;
        margin: 0.7rem 0;
        .otherchat {
            width: 100%;
            position: relative;
            .img {
                width: 0.6rem;
                height: 0.6rem;
                border-radius: 50%;
                position: absolute;
                top: 50%;
                left: 0.2rem;
                transform: translateY(-50%);
                cursor: pointer;
            }
            .nt {
                font-size: 0.25rem;
                left: 1rem;
                top: -0.4rem;
                position: absolute;
                color: #686868;
                span {
                    padding-right: 0.2rem;
                }
                span:nth-child(2) {
                    font-size: 0.2rem;
                }
            }
            .msg {
                float: left;
                max-width: 60%;
                //  margin-top: 0.2rem;
                margin-left: 1rem;
                padding: 0.12rem;
                border-radius: 0.1rem;
                font-size: 0.28rem;
                line-height: 0.46rem;
                background-color: #fff;
                word-break: break-all;
                letter-spacing: 1px;
            }
        }
        .mychat {
            width: 100%;
            position: relative;
            .img {
                width: 0.6rem;
                height: 0.6rem;
                border-radius: 50%;
                right: 0;
                position: absolute;
                top: 50%;
                right: 0.2rem;
                transform: translateY(-50%);
            }
            .nt {
                font-size: 0.25rem;
                right:1rem;
                top: -0.4rem;
                position: absolute;
                color: #686868;
                span {
                    padding-left: 0.2rem;
                }
                span:nth-child(1) {
                    font-size: 0.2rem;
                }
            }
            .msg {
                float: right;
                max-width: 60%;
                margin-right: 1rem;
                padding: 0.12rem;
                border-radius: 0.1rem;
                font-size: 0.28rem;
                line-height: 0.46rem;
                background-color: #4290F7;
                color: #fff;
                word-break: break-all;
              letter-spacing: 1px;
            }
        }
    }
</style>
