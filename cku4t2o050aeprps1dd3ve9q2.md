## Upgrade your Terminal to 'Zsh for Humans' by @romkatv

Roman Perepelitsa has coded a fantastic, featureful `zsh` configuration that works right out of the box. "[Zsh for Humans](https://github.com/romkatv/zsh4humans)" (aka "z4h") and its companion prompt "[Powerlevel10k](https://github.com/romkatv/powerlevel10k)" are easy to install, and come configured with the most useful features you might need in an interactive prompt. You can see what my configuration of the prompt looks like here: 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632876831495/EGYVkd1Bq.png)

I love the ssh wrapper feature, which lets you auto-push your zsh environment up to a remote server. You use the wrapper like this: 

```
% z4h ssh myuser@thehost.com
```

My daily driver is macOS, so I needed to tweak some settings in my terminals to get the key bindings to work as expected: 

* iTerm2:
   1. iTerm, Prefs, Profiles (select your profile), Keys, then…   
   2. Right/Left option key: Esc+
* Kitty:
   1. In the config file: `macos_option_as_alt yes`

Now you can enter a command like history and before hitting Enter, press Alt-H to show help for that command.

%[https://github.com/romkatv/zsh4humans]
%[https://github.com/romkatv/powerlevel10k]


* * * 
Photo by <a href="https://unsplash.com/@hudsoncrafted?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Debby Hudson</a> on <a href="https://unsplash.com/s/photos/type?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
  