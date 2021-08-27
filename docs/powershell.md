# PowerShell の設定

Windows PowerShell と Windows Terminal の両方で以下のことをする。

- Powerline をセットアップ
- Dracula テーマを適用

## Powerline をセットアップ

### Posh-Git と Oh-My-Posh をインストール

```powershell
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
```

### プロファイルを編集

`~\Documents\PowerShell\Microsoft.PowerShell_profile.ps1`に以下のスクリプトを追加する。
使用できるテーマは`Get-PoshThemes`から確認可能。

=== "Microsoft.PowerShell_profile.ps1"

```powershell
Import-Module posh-git
Import-Module oh-my-posh
Set-PoshPrompt -Theme Paradox
```

### フォント

Powerline に対応したフォントをインストールする。フォントは 1 種類しか指定できないため、和文も含まれている方が望ましい。
[HackGen Console](https://github.com/yuru7/HackGen)が良さそう。

## Dracula テーマを適用

Dracula がベストかはわからないが、他に良いものを探すのがめんどくさいので。

### Windows Terminal

WindowsTerminal の設定から json ファイルを開き、[公式の説明](https://draculatheme.com/windows-terminal)にあるスクリプトを追加する。
ついでにフォントを HackGen Console にしておく。

### Windows PowerShell

[公式の説明](https://draculatheme.com/powershell)通りにやる。
プロファイルは GitPromptSettings の部分は省いてもよさそう。

## サジェストを有効にする

サジェストは PSReabLine 2.1 から使用できる。必要であれば v2.1 以上にアップデートする。

```powershell
(Get-Module PSReadLine).Version
Install-Module -Name PSReadLine -RequiredVersion 2.1.0
```

プロファイルに以下を記載することで有効になる。

=== "Microsoft.PowerShell_profile.ps1"

```powershell
Set-PSReadLineOption -PredictionSource History
```

## 参照

- [Windows ターミナル Powerline のセットアップ | Microsoft Docs](https://docs.microsoft.com/ja-jp/windows/terminal/tutorials/powerline-setup)
- [PowerShell | Oh My Posh](https://ohmyposh.dev/docs/pwsh)
- [[PowerShell] Oh my Posh (Powerline) を使って PowerShell コンソールをおしゃれにカスタマイズする | DevelopersIO](https://dev.classmethod.jp/articles/customize-your-powershell-console-with-oh-my-posh3/)
- [Windows Terminal で Powerline の環境を整える - ビー鉄のブログ](https://www.beeete2.com/blog/?p=2619)
- [[PowerShell] PSReadLine 2.1 がリリースされました | DevelopersIO](https://dev.classmethod.jp/articles/powershell-psreadline-21-released/)
- [PSReadLine について - PowerShell | Microsoft Docs](https://docs.microsoft.com/ja-jp/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1)
