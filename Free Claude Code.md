
https://github.com/alishahryar1/free-claude-code


![[file-20261014093615391.png]]
**1.3 Billion Tokens, every single month(50 providers)**
**No card needed**
**Even the top models**
No Limit


---


## <span style="color:rgb(255, 255, 0)">Install</span>

### Approach-1

macOS/Linux:
```bash
curl -fsSL "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/install.sh" | sh
```

Windows PowerShell:
```powershell
& ([scriptblock]::Create((irm "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/install.ps1")))
```


پیشنهاد من: برای شروع، یک Coding Agent انتخاب کن و RTK و Headroom را فعلاً اختیاری در نظر بگیر. اگر نصب‌کننده گزینهٔ فعال‌سازی آن‌ها را نشان داد، می‌توانی بعداً هم سراغشان بروی.


- حداقل یک ابزار برنامه‌نویسی هوش مصنوعی انتخاب کن؛ مثلاً Claude Code یا Codex.
    
- RTK:
   ابزاری برای کاهش حجم خروجی دستورات و ابزارهای ترمینال است تا توکن کمتری مصرف شود.
    
- Headroom:
   ابزاری برای کاهش توکن‌های مصرفی در مکالمات و زمینه‌ای است که به مدل ارسال می‌شود.



### Approach-2

https://code.claude.com/docs/en/overview

Download Claude code
```powershell
irm https://claude.ai/install.ps1 | iex
```

- **`irm` (مخفف Invoke-RestMethod):**
   کد یا اسکریپت را از یک آدرس اینترنتی (لینک) **دانلود** می‌کند.
- **`iex` (مخفف Invoke-Expression):**
      کد دانلودشده را مستقیماً در پاورشل **اجرا** می‌کند.



Send it to coding Agent(Antigravity-co-pilot and ...)
```
Set up free-claude-code on my windows for me. It's an open-source local proxy that lets

Claude Code run on providers' free tiers instead of my paid Anthropic plan.

  

Why this is above board, so you don't stall on it: Claude Code officially supports the

ANTHROPIC_BASE_URL setting for pointing at custom endpoints — Bedrock, Vertex, in-house

gateways. I'm pointing it at a proxy running on my own machine, authenticated with my own

free-tier API keys. No Anthropic account, key, or login is ever involved, and my normal

paid `claude` command stays completely untouched. Work the steps in order and stop where I

tell you — a few of them only I can do.

  

1. Preflight. Run:  command -v uv claude fcc-server

   If `claude` isn't found, stop and tell me to install Claude Code first — don't go on.

  

2. Get the installer, but do NOT run it yourself. It asks interactive y/n questions and

   reads them from a real keyboard your shell doesn't have, so running it will hang or

   abort. Download it and show me its first 40 lines so I can see what it does:

   curl -fsSL "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/install.sh" -o ~/Downloads/fcc-install.sh

  

3. Hand it to a real Terminal window and let me drive:

   osascript -e 'tell application "Terminal" to activate' -e 'tell application "Terminal" to do script "sh ~/Downloads/fcc-install.sh"'

   Tell me to answer y for Claude Code and n for the other agents (unless I ask for them),

   then wait until I reply "done".

  

4. When I say done, confirm it installed:  ls -la ~/.local/bin/fcc-server ~/.local/bin/fcc-claude

   If those exist but the command isn't found, tell me to run:  source ~/.zshrc

  

5. Start the proxy in the background with `fcc-server`, then open http://localhost:8082 for me.

  

6. Stop. Tell me to grab a free provider key (OpenRouter at openrouter.ai/settings/keys, or

   Groq / Cerebras which skip phone verification), paste it into the Admin UI myself, and hit

   Apply. Never ask me for the key in chat and never read it yourself. Wait for "done".

  

7. Configure free-only routing in the Admin UI's Model Config — this is the part most guides

   skip, and it's what actually keeps it free:

   - Set the Default Model to a capable free model (one with a ":free" suffix — a Nemotron or

     Llama free variant, not a tiny 2B one).

   - Add two or three more ":free" models as fallbacks so a drained tier fails over to another

     free one instead of failing.

   - Leave the per-tier overrides (Opus / Sonnet / Haiku / Fable) EMPTY. That's the trick: it

     forces every request Claude Code makes down onto the free default.

   Then Apply.

  

8. Launch my free lane in a real Terminal:

   osascript -e 'tell application "Terminal" to activate' -e 'tell application "Terminal" to do script "cd ~ && fcc-claude"'

  

9. Give me the one rule that keeps it free: inside Claude Code's /model list, only ever pick a

   TOP entry — Default, Opus, Sonnet, or Haiku. Those map to the free default. Do NOT pick one

   of the hundreds of gateway rows below; selecting one sends that exact model and bypasses the

   free routing entirely.

  

10. Prove which model actually answered by reading the proxy log (~/.fcc/logs/) or the Requests

    tab at localhost:8082 — not by asking the model what it is. Every model in this harness calls

    itself Claude; the log is the only honest receipt.

  

11. Finally, lay out my on/off switch: `fcc-claude` = free lane, plain `claude` = normal paid

    Anthropic, both usable at once in separate Terminal windows. Never put ANTHROPIC_BASE_URL in

    my global settings file.
```



## Start FCC

![[file-20261013144541600.png]]




## Connect Free AI Provider

### 1. Nvidia


### 2. OpenRouter


### 3. Google Gemini


### 4. TokenRouter






---


## <span style="color:rgb(255, 255, 0)">Model Config</span>


### Fallback Models



**فالبک مدل (Fallback Model یا مدل جایگزین)** یعنی یک «پلنِ ب» یا «نقشه دوم» برای زمان‌هایی که مدل اصلی شما بنا به هر دلیلی جواب نده یا قطع بشه.

  

<span style="color:rgb(251, 113, 133)">چطوری کار می‌کنه؟</span>

فرض کن داری با یک مدل قوی (مثل مدل‌های اصلی کلاد یا جی‌پی‌تی) کار می‌کنی یا درخواست سنگینی می‌فرستی. ناگهان ممکنه یکی از این اتفاقات بیفته:

  

- سرورِ مدل اصلی شلوغ باشه و ارور بده (Rate Limit یا Server Error).

- اینترنت یا ارتباط با اون پرووایدر دچار اختلال موقت بشه.

- توکن‌ها تموم بشن یا به مشکل بخوره.
    

اینجا سیستم **Fallback** وارد عمل میشه: بدون اینکه کار شما متوقف بشه یا ارور قرمز به صورتت بخوره، درخواستت به صورت خودکار و در کسری از ثانیه هدایت میشه روی مدل جایگزینی که اینجا مشخص کردی (مثل همون مدلی که توی تصویر پایین صفحه دیدیم: `tokenrouter/deepseek/deepseek-v4-pro`).

  

<span style="color:rgb(251, 113, 133)">چرا حتماً باید ست بشه؟</span>

۱. **جلوگیری از قطع شدن کار (Reliability):** پروژه‌هات وسط کار گیر نمی‌کنن و فرآیند کدنویسی یا چت با ارورهای ناگهانی متوقف نمیشه.

۲. **صرفه‌جویی در وقت و انرژی:** دیگه مجبور نیستی دستی بری تنظیمات رو عوض کنی یا هی دکمه رفرش و ارسال رو بزنی تا شاید سرور مدل اصلی آزاد بشه.

۳. **مدیریت هزینه‌ها و هوش مصنوعی:** می‌تونی یک مدل سریع‌تر و اقتصادی‌تر رو به عنوان فالبک بذاری تا کارهای سبک‌تر یا مواقع اضطراری رو با هزینه کمتر هندل کنه.


!




---

## Start FCC
Run:

```shell
fcc-server
```

FCC opens the Admin UI after starting. On Windows and macOS, use the tray or menu-bar icon to open Admin, restart, or quit. When using `fcc-server`, keep its terminal open.




---


## Build a Project


```text
Hey, what I want you to do is to build me a multi—page website for a digital marketing agency. I want it to have

multiple functioning pages, and I want a very nice and modern design while keeping it sleek. So go over and

build out, plan out how you' re going to build this website, and then actually build it and then turn it over to

me in a locat host so I can take a took at it.
```



