# enable-chrome-ask-gemini｜开启chrome ask gemini功能
A practical method for non-US chrome users to enable chrome ai functions
一个适用于非美国地区chrome用户打开ai功能的方法

If you want to use these functions: 如果你想使用这些功能：

<img width="142" height="44" alt="Screenshot 2026-05-24 at 14 49 29" src="https://github.com/user-attachments/assets/68331f7b-730d-49b8-9518-0460e50b03e5" />

Or they suddenly disappeared 或者这些功能突然消失了

## Solution｜解决方案
For MacOS users: Run this in Terminal｜Mac用户：在终端运行这个

`sed -i '' -e 's/"variations_country":"[^"]*"/"variations_country":"us"/g' -e 's/"is_glic_eligible":false/"is_glic_eligible":true/g' "$HOME/Library/Application Support/Google/Chrome/Local State"`

For Windows users: Run this in powershell｜Windows用户：在powershell运行这个

`$path = "$env:LOCALAPPDATA\Google\Chrome\User Data\Local State"; (Get-Content $path -Raw) -replace '"variations_country":"[^"]*"', '"variations_country":"us"' -replace '"is_glic_eligible":false', '"is_glic_eligible":true' | Set-Content $path -NoNewline`

What's more, make sure you are always using system proxy of regions where ai functions can be used.

## How it works｜原理 Summarized by ai
问题所在 (The Problem)：Chrome 在启动时，如果发现你的网络不在美国，就会在后台把一个“隐形开关”关掉，导致 AI 按钮彻底消失。When Chrome starts, if it detects you are not in the US, it turns off a "hidden switch" in the background, causing the AI button to vanish completely.

文件的秘密 (The Secret File)：Chrome 会把这个“隐形开关”的状态，记录在电脑里的一个叫 Local State 的文本文件里。Chrome records the status of this "hidden switch" inside a local text file called Local State.

命令的作用 (What the Command Does)：这行命令不需要你手动打开文件，它像一个全自动的修改器，直接钻进文件内部，强制做了两件事：Without making you open the file manually, this command acts like an automatic cheat code. It goes inside the file and forces two changes:把“当前国家”改成 美国 (us)。Changes "current country" to US.把“AI 资格”从“关闭”改成 开启 (true)。Changes "AI eligibility" from "false" to true.
