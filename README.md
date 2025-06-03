# How to Setup Windows 11

Windows 11 をクリーンインストールした直後の環境から、`winget` の構成ファイル（`.dsc.yaml`）を適用して環境構築するまでの手順を記録しておく。

## 1. App Installer（WinGet）のインストール

Windows 初期状態には `winget` が入っていない場合がある。こちらで入手してインストールする: https://learn.microsoft.com/en-us/windows/msix/app-installer/install-update-app-installer

インストール完了後、次のコマンドで確認できる：

```powershell
winget --version
```

## 2. PowerShell 7 のインストール

`winget configure` は PowerShell 7.x 以降が必要。
こちらで入手してインストールする: https://github.com/PowerShell/PowerShell/releases

インストール後、「PowerShell 7 (x64)」 を起動して確認:

```powershell
$PSVersionTable.PSVersion
```

出力が 7.x.x になっていればOK。

## 3. 必要なDSCモジュールのインストール

以下のコマンドを PowerShell 7 上で実行: 

```powershell
Install-Module Microsoft.WinGet.DSC -Force
Install-Module PSDscResources -Force
Install-Module DSCR_Font -Force
```

## 4. 構成ファイルの適用

このリポジトリの `configuration.dsc.yaml` をダウンロードして適用する:

```powershell
winget configure --file .\configuration.dsc.yaml
```

※OSデフォルトの「Windows Powershell」で実行しないよう注意
