# 二奢商家AI助手

7×24小时解答入驻、运营、转化、合规、鉴定等所有经营问题

<ClientOnly>
  <div class="ai-chat-box" id="chatBox">
    <div class="ai-message">你好，我是二奢商家AI助手，有什么可以帮你？</div>
    <div class="clearfix"></div>
  </div>

  <div class="input-group">
    <input type="text" id="userInput" class="form-control" placeholder="请输入你的问题...">
    <button class="btn btn-brand" id="sendBtn">发送</button>
  </div>
</ClientOnly>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  const chatBox = document.getElementById('chatBox')
  const userInput = document.getElementById('userInput')
  const sendBtn = document.getElementById('sendBtn')
  if (!chatBox || !userInput || !sendBtn) return

  function sendMessage() {
    const msg = userInput.value.trim()
    if (!msg) return
    chatBox.innerHTML += `<div class="user-message">${msg}</div><div class="clearfix"></div>`
    userInput.value = ''
    setTimeout(() => {
      let reply = "我是二奢商家AI助手，可解答入驻、运营、合规、鉴定问题哦！"
      if (msg.includes('入驻')) reply = "入驻免费，需营业执照+正品货源，4步完成开通~"
      if (msg.includes('运营')) reply = "二奢运营核心：实拍开箱+鉴定视频+精准话题！"
      if (msg.includes('鉴定')) reply = "所有商品必须支持中检/国检鉴定，合规经营！"
      chatBox.innerHTML += `<div class="ai-message">${reply}</div><div class="clearfix"></div>`
      chatBox.scrollTop = chatBox.scrollHeight
    }, 800)
  }

  sendBtn.addEventListener('click', sendMessage)
  userInput.addEventListener('keypress', e => e.key === 'Enter' && sendMessage())
})
</script>
