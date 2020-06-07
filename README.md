# Move WSL2 Ubuntu 20.04 LTS to a different drive/partition 

1. Install LxRunOffline using [choco](https://chocolatey.org/)
```console
PS C:\> choco install lxrunoffline -y
```

2. Install [Ubuntu-20.04 LTS](https://www.microsoft.com/store/productId/9N6SVWS3RX71) from Microsoft Store

3. Create new folder under new drive with permissions (I'm using PowerShell)
```console
PS C:\> whoami
<pc-name>\<user>
# Example:
# PS C:\> whoami
# amit-pc\afeldman

PS C:\> icacls <drive-letter>:\<new-folder-name> /grant "<user>:(OI)(CI)(F)"
# Example:
# PS C:\> icacls D:\wsl /grant "afeldman:(OI)(CI)(F)"
```

4. Move Ubuntu 20.04 LTS distribution using `lxrunoffline move` (it takes a while to complete)
```console
PS C:\> lxrunoffline move -n Ubuntu-20.04 -d <drive-letter>:\wsl\installed\Ubuntu-20.04
# Example:
# PS  C:\> lxrunoffline move -n Ubuntu-20.04 -d D:\wsl\installed\Ubuntu-20.04
```

5. Check installation folder
```console
PS C:\> lxrunoffline get-dir -n Ubuntu-20.04
D:\wsl\installed\Ubuntu-20.04
```

6. Run Ubuntu-20.04 LTS distribution
```console
PS C:\> lxrunoffline run -n Ubuntu-20.04 -w
afeldman@AMIT-PC:/mnt/c/Users/afeldman$
# or running
# PS C:\> wsl
```

[Original Post](https://superuser.com/a/1347319)
