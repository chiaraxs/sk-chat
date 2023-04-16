<template>
  <div class="main main-container">
    <div class="container-fluid">
      <div class="storykube-chat-container container">

        <!-- Row one: chat messages -->
        <div class="row pt-2">

          <!-- Col one -->
          <div class="col-xl-3 col-sm-12">
            <div class="container-col-sx px-1 mt-2 d-flex justify-content-end">
              <a href="#" class="text-decoration-none">
                <span class="text-white">
                  <i class="fa-solid fa-arrow-left-long"></i>
                  <span class="ms-3 fw-bold">Leave the chat</span>
                </span>
              </a>
            </div>
          </div>
          <!-- /Col one -->

          <!-- Col two -->
          <div class="col-xl-6 col-sm-12 chat-messages-container">
            <!-- Message 1-->
            <div class="row supernova-chat-message mt-2 p-4 rounded">
              <div class="supernova-info-chat d-flex">
                <div class="supernova-img">
                  <img src="../assets/supernova-icon.png" alt="supernova-img" />
                </div>

                <div class="supernova-text-chat ms-3">
                  <p class="text-white">
                    Hi, I'm Supernova and I can help you writing. What I can write for you?
                  </p>
                  <a href="#" class="link-secondary fw-bold">
                    Let's have some inspiration.
                  </a>
                </div>
              </div>
            </div>

            <!-- Message 2-->
            <div class="row user-chat-message mt-2 p-4 rounded">
              <div class="user-info-chat d-flex">
                <div class="user-img">
                  <img src="../assets/user-icon.png" alt="user-img" />
                </div>

                <div class="user-text-chat ms-3">
                  <p class="text-white">ciao</p>
                </div>
              </div>
            </div>

            <!-- Message 3-->
            <div class="row supernova-chat-message mt-2 p-4 rounded">
              <div class="supernove-info-chat d-flex">
                <div class="supernova-img">
                  <img
                    src="../assets/supernova-icon.png"
                    alt="supernova-img"
                  />
                </div>

                <div class="supernova-text-chat ms-3">
                  <p class="text-white">Ciao, in cosa posso aiutarti?</p>
                  <span>
                    <i class="fa-solid fa-file-arrow-down copy-chat-link"></i>
                  </span>
                  <a href="#" class="copy-chat-link fw-bold ps-2">
                    Copy to editor
                  </a>
                </div>
              </div>

              <div class="accuracy-container d-flex justify-content-end">
                <span class="accuracy-text fw-bold">Accuracy: 98.81%</span>
              </div>
            </div>
          </div>
          <!-- /Col two-->

          <!-- Col three-->
          <div class="container-col-dx col-xl-3 col-sm-12 mt-2">
            <div class="sk-logo-container">
              <img src="../assets/sk_logo.png" alt="storykube-logo" />
            </div>
          </div>
          <!-- /Col three-->
        </div>
        <!-- /Row one -->

        <!-- Row two: chat input text -->
        <div class="row">

          <!-- Col empty-->
          <div class="col-lg-3 col-sm-12"></div>

          <!-- Col input text chat message-->
          <div class="col-xl-6 col-sm-12">
            <div class="input-chat-container fixed-bottom d-flex justify-content-center">
              <div class="input-message py-3">
                <div class="reset-icon-container text-white d-flex justify-content-center">
                  <span>
                    <i class="fa-solid fa-rotate-right p-1"></i>
                    Reset
                  </span>
                </div>

                <div class="max-text-container d-flex justify-content-end text-secondary">
                  <span class="max-text py-2">0/2000</span>
                </div>

                <div class="input-group position-relative">
                  <input
                    v-model="message"
                    type="text"
                    placeholder="Write something..."
                    class="input-chat p-2"
                    @keyup.enter="sendMessage"
                  />
                  <span>
                    <i class="fa-solid fa-rotate-right chat-reset-icon text-success"></i>
                  </span>
                  <span>
                    <i
                      @click="sendMessage"
                      class="fas fa-paper-plane send-chat-icon text-primary"
                    ></i>
                  </span>
                </div>
              </div>
            </div>
          </div>

          <!-- Col empty-->
          <div class="col-lg-3 col-sm-12 mt-2"></div>
        </div>
        <!-- /Row two -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainContent",
  data() {
    return {
      message: "",
    };
  },
  methods: {
    sendMessage() {
      if (this.message !== "") {
        const newMessage = document.createElement("div");
        newMessage.innerHTML = `
            <div class="row user-chat-message mt-2 p-4 rounded" style="background-color:#2C2C2C;">
              <div class="user-info-chat d-flex">
                <div class="user-img">
                  <img src="../assets/user-icon.png" alt="user-img" width="">
                </div>
                <div class="user-text-chat ms-3">
                  <p class="text-white">${this.message}</p>
                </div>
              </div>
              </div>
            `;
        const chatMessages = document.querySelector(".chat-messages-container");
        chatMessages.appendChild(newMessage);
        // Reset input della chat
        this.message = "";
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/variables.scss";

.main {
  height: 100vh;
  background-color: $bg-main;
}

// Chat-container
.supernova-img img, .user-img img {
  width: 30px;
}

.copy-chat-link {
  font-size: 12px;
  color: $copy-chat-link;
}

.sk-logo-container img {
  margin: -20px;
  width: 120px;
}

.accuracy-text {
  font-size: 11px;
  color: $accuracy-text;
}

// Chat bg
.supernova-chat-message {
  background-color: $bg-supernova-chat;
}

.user-chat-message {
  background-color: $bg-user-chat;
}

// Chat input
.input-chat{
  width: 650px;
}

.send-chat-icon {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
}

.chat-reset-icon {
  position: absolute;
  right: 35px;
  top: 50%;
  transform: translateY(-50%);
}
</style>
