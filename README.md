<p align=center>
<br>
<a href="http://makeapullrequest.com"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg"></a>
<img src="https://img.shields.io/badge/os-linux-brightgreen">
<img src="https://img.shields.io/badge/os-mac-brightgreen">
<img src="https://img.shields.io/badge/os-windows-brightgreen">
<img src="https://img.shields.io/badge/os-android-brightgreen">
<br>
<h1 align="center">
<a href="https://discord.gg/aqu7GpqVmR">
<img src="https://invidget.switchblade.xyz/aqu7GpqVmR">
</a>
<br>
<a href="https://github.com/port19x"><img src="https://img.shields.io/badge/lead-port19x-lightblue"></a>
<a href="https://github.com/CoolnsX"><img src="https://img.shields.io/badge/maintainer-CoolnsX-blue"></a>
<a href="https://github.com/justchokingaround"><img src="https://img.shields.io/badge/maintainer-justchokingaround-blue"></a>
<a href="https://github.com/Derisis13"><img src="https://img.shields.io/badge/maintainer-Derisis13-blue"></a>
<a href="https://github.com/71zenith"><img src="https://img.shields.io/badge/maintainer-71zenith-blue"></a>

</p>

<h3 align="center">
Animelere göz atmak ve izlemek için bir cli (yalnız VE arkadaşlarla). Bu araç <a href="https://allanime.to/">allanime</a> sitesini kazır. 
</h3>
	
<h1 align="center">
	Vitrin
</h1>

[ani-cli-demo.webm](https://user-images.githubusercontent.com/44473782/224679247-0856e652-f187-4865-bbcf-5a8e5cf830da.webm)

## İçindekiler

- [Hataları düzeltme]( #Hataları-düzeltme)
- [Kur](#Kurulum)
  - [Linux](#Linux)
   - [Debian](#Debian-unstable)
   - [Fedora](#Fedora)
   - [Arch](#Arch)
   - [OpenSuse Tumbleweed ve Leap](#OpenSuse-Tumbleweed-ve-Leap)
   - [Kaynaktan](#Kaynaktan-kurulum)
  - [MacOS](#MacOS)
  - [Windows](#Windows)
  - [Android](#Android)
  - [Steam Deck](#Steam-deck)
- [Kaldırma]( #Kaldırma)
- [Bağımlılıklar](#Bağımlılıklar)
- [Kankalar](#Kankalar)
- [Katkı Yönergeleri](./CONTRIBUTING.md)
- [Yasal Uyarı](./disclaimer.md)

## Hataları düzeltme

"Video url bulunamadı" veya herhangi bir kırılma sorunuyla karşılaşırsanız, en son sürümde olduğunuzdan emin olun.
Linux, Mac ve Android'de güncellemek için `sudo ani-cli -U` komutunu kullanın. Windows'ta gitbash'i yönetici olarak çalıştırın ve ardından `ani-cli -U` yazın.
Bundan sonra sorun devam ederse bir "issue" açın. (Lütfen burada değil, pystardust'ın hesabında issue açın. Ben sadece çevirisini yapıyorum.)

Geçmiş yeniden işlendi ve yeniden konumlandırıldı. Bir geçiş betiği üzerinde çalışıyoruz, lütfen sabırlı olun. Eski geçmiş `less ${XDG_CACHE_HOME:-$HOME/.cache}/ani-hsts` komutu ile görüntülenebilir

## Kurulum

#### V3.2 veya v3.2.x serisi kullanıcıları yükseltme yapmadan önce scripti kaldırmalıdır
Aksi takdirde aşağıdaki gibi bir hata görmeniz muhtemeldir: ` "/usr/bin/ani-cli: satır 470: (...)/player_mpv: Böyle bir dosya veya dizin yok"`

### Yerel paketler

[![Paketleme durumu](https://repology.org/badge/vertical-allrepos/ani-cli.svg?minversion=4.0)](https://repology.org/project/ani-cli/versions)

*Yerel paketler daha sağlam bir güncelleme döngüsüne sahiptir, ancak bazen yükseltmeleri yavaş olabilir. Platformunuz için olan güncelse, onunla devam etmenizi öneririz.*

### Linux

#### Debian unstable

```sh
sudo apt install ani-cli
```

#### Fedora

mpv (ve vlc) yüklemek için _RPM Fusion free_ etkinleştirilmiş olmalıdır. Basitçe buradaki talimatları izleyin: https://rpmfusion.org/Configuration
Syncplay'i yükleyebilmek için bu copr reposunu etkinleştirmeniz gerekir (talimatlar dahildir): https://copr.fedorainfracloud.org/coprs/batmanfeynman/syncplay/.

ani-cli'yi yüklemek için:
```sh
sudo dnf copr enable derisis13/ani-cli
sudo dnf install ani-cli
```
*Dağıtımınız için rpm kullanıyorsanız ve yerel bir paket görmek istiyorsanız, bir "issue" açın.*

#### Arch

AUR'den oluşturun ve kurun: 
```sh
yay -S ani-cli
```
Ayrıca şunu da göz önünde bulundurun `ani-cli-git`

#### Gentoo

GURU'dan oluşturun ve kurun:
```sh
sudo eselect repository enable guru
sudo emaint sync -r guru
sudo emerge -a ani-cli
```
9999 ebuild kullanmayı göz önünde bulundurun.
```sh
sudo emerge -a =app-misc/ani-cli-9999
```

#### OpenSuse Tumbleweed ve Leap

Suse'de sağlanan MPV ve VLC paketlerinde ani-cli tarafından kullanılan özellikler eksiktir. Gerekli olan tek şey, her Suse sürümü için sürümleri olan "Only Essentials" deposudur.
Bununla ilgili talimatları [burada](https://en.opensuse.org/Additional_package_repositories#Packman) bulabilirsiniz.

ani-cli copr reposunu eklemek için, güncelleyin ve ardından ani-cli run'ı yükleyin (her iki sürümde de böyledir):
```sh
zypper addrepo https://download.copr.fedorainfracloud.org/results/derisis13/ani-cli/opensuse-tumbleweed-x86_64/ ani-cli
zypper dup
zypper install ani-cli
```
İmza doğrulama başarısız oldu [4-İmzalar ortak anahtarı mevcut değil]` uyarısı alacaksınız, ancak bu durum komut isteminden göz ardı edilebilir.

*Not: paket noarch'tır, bu nedenle depo x86-64 olarak etiketlenmiş olsa bile herhangi bir mimaride çalışmalıdır*

#### Kaynaktan kurulum

Bağımlılıkları kurun [(Aşağıya bakın)](#Bağımlılıklar)

```sh
sudo rm -rf "/usr/local/share/ani-cli" "/usr/local/bin/ani-cli" "/usr/local/bin/UI" /usr/local/bin/player_* #Bunlardan bazıları bulunmazsa sorun değil
git clone "https://github.com/Agayev033/ani-cli.git"
sudo cp ani-cli/ani-cli /usr/local/bin
rm -rf ani-cli
```

### MacOS

Bağımlılıkları kurun [(Aşağıya bakın)](#Bağımlılıklar)

Kurulu değilse [HomeBrew] (https://docs.brew.sh/Installation) kurun.

```sh
rm -rf "$(brew --prefix)/share/ani-cli" "$(brew --prefix)/bin/ani-cli" "$(brew --prefix)/bin/UI" "$(brew --prefix)"/bin/player_* #Bunlardan bazıları bulunmazsa sorun olmaz
git clone "https://github.com/Agayev033/ani-cli.git" && cd ./ani-cli
cp ./ani-cli "$(brew --prefix)"/bin 
cd .. && rm -rf ./ani-cli
```

*Mac OS'de gerekli olan bağımlılıkları (Homebrew ile) yüklemek için çalıştırabilirsiniz:* 

```sh
brew install curl grep aria2 ffmpeg git fzf && \
brew install --cask iina
``` 
*Neden mpv değil de iina? MacOS için mpv'nin yerine geçer. OSX kullanıcı arayüzü ile iyi entegre olur. M1 için mükemmel desteği var ve ayrıca Açık Kaynak.*  

### Windows

*ani-cli bir posix kabuğuna ihtiyaç duyar ve mevcut yolu git bash'tir. Ne yazık ki fzf git bash'in varsayılan terminalinde çalışamaz. Çözüm windows terminalinde git bash kullanmaktır*

İlk olarak, Windows terminal önizlemesine ihtiyacınız olacak. [(Yükle)](https://apps.microsoft.com/store/detail/windows-terminal-preview/9N8G5RFZ9XK3?hl=de-at&gl=at&rtc=1)

Ardından git bash'in kurulu olduğundan emin olun. [(Yükle)](https://git-scm.com/download/win) Windows terminaline eklenmesi gerekiyor [(Talimatlar)](https://stackoverflow.com/questions/56839307/adding-git-bash-to-the-new-windows-terminal)

Aşağıdaki adımların ve ani-cli'nin windows terminalinde git bash'ten çalıştırılması gerekir. 

#### Scoop bucket

```sh
scoop bucket add extras
scoop install ani-cli
```

#### Kaynaktan
```sh
rm -rf "/usr/local/share/ani-cli" "/usr/local/bin/ani-cli" "/usr/local/bin/UI" /usr/local/bin/player_* #Bunlardan bazıları bulunmazsa sorun olmaz
git clone "https://github.com/Agayev033/ani-cli.git"
cp ani-cli/ani-cli /usr/bin
rm -rf ani-cli
```

#### Bağımlılıklar

Tüm bağımlılıklar scoop ile yüklenebilir (ekstralar bucket'inden), ancak bazı kullanıcılar yüklenen programların her zaman yola eklenmediğini deneyimlemiştir. Böyle bir durumda bunun yerine winget'ten yükleme yapmak genellikle işe yarar.

### Android

termux'u yükleyin [(Kılavuz)](https://termux.com/)

#### Termux paketi

```sh
pkg up -y
pkg install ani-cli
```

#### Kaynaktan

```sh
pkg up -y
rm -rf "$PREFIX/share/ani-cli" "$PREFIX/bin/ani-cli" "$PREFIX/bin/UI" "$PREFIX"/local/bin/player_* #Bunlardan bazıları bulunmazsa sorun değil
git clone "https://github.com/Agayev033/ani-cli.git"
cp ani-cli/ani-cli "$PREFIX"/bin
rm -rf ani-cli
```

Oynatıcılar için mpv ve vlc'nin apk (playstore/fdroid) sürümlerini kullanabilirsiniz. Bunların termux'tan kontrol edilemeyeceğini unutmayın, bu nedenle bağımlılıkları kontrol ederken bir uyarı oluşturulur.

### Steam Deck

#### Kopyala yapıştır script:

* Masaüstü moduna geçme (`STEAM` Düğmesi > Güç > Masaüstüne Geç)
* `Konsole`u açın (Sol alt köşedeki Steam Deck Simgesi > Sistem > Konsole)
* Komut dosyasını kopyalayın, CLI'ya yapıştırın ve Enter'a basın (Steam Deck üzerindeki "A" düğmesi) 

```sh
[ ! -d ~/.local/bin ] && mkdir ~/.local/bin && echo "export $PATH=$HOME/.local/bin:$PATH" >> ".$(echo $SHELL | sed -nE "s|.*/(.*)\$|\1|p")rc" 

git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install

mkdir ~/.aria2c
curl -o ~/.aria2c/aria2-1.36.0.tar.bz2 https://github.com/q3aql/aria2-static-builds/releases/download/v1.36.0/aria2-1.36.0-linux-gnu-64bit-build1.tar.bz2
tar xvf ~/.aria2c/aria2-1.36.0.tar.bz2 -C ~/.aria2c/
cp ~/.aria2c/aria2-1.36.0-linux-gnu-64bit-build1/aria2c ~/.local/bin/
chmod +x ~/.local/bin/aria2c

git clone https://github.com/Agayev033/ani-cli.git ~/.ani-cli
cp ~/.ani-cli/ani-cli ~/.local/bin/

flatpak install io.mpv.Mpv
```
sorularda enter tuşuna basın (Steam Deck'te "A" düğmesi)

#### Adım adım kurulum:

##### mpv'yi yükleyin (Flatpak sürümü):

```sh
flatpak install io.mpv.Mpv
```
sorularda enter tuşuna basın (Steam Deck'te "A" düğmesi)

##### [fzf] Kurun (https://github.com/junegunn/fzf): 

```sh
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```
sorularda enter tuşuna basın (Steam Deck'te "A" düğmesi)

##### Eğer yoksa bir ~/.local/bin klasörü oluşturun ve $PATH'e ekleyin

```sh
[ ! -d ~/.local/bin ] && mkdir ~/.local/bin && echo "export $PATH=$HOME/.local/bin:$PATH" >> ".$(echo $SHELL | sed -nE "s|.*/(.*)\$|\1|p")rc"  
```

##### [aria2](https://github.com/aria2/aria2) yükleyin (yalnızca indirme özelliği için gereklidir):

```sh
mkdir ~/.aria2c
curl -o ~/.aria2c/aria2-1.36.0.tar.bz2 https://github.com/q3aql/aria2-static-builds/releases/download/v1.36.0/aria2-1.36.0-linux-gnu-64bit-build1.tar.bz2
tar xvf ~/.aria2c/aria2-1.36.0.tar.bz2 -C ~/.aria2c/
cp ~/.aria2c/aria2-1.36.0-linux-gnu-64bit-build1/aria2c ~/.local/bin/
chmod +x ~/.local/bin/aria2c
```

##### Ani-cli kurun:

```sh
git clone https://github.com/Agayev033/ani-cli.git ~/.ani-cli
cp ~/.ani-cli/ani-cli ~/.local/bin/
```

##### Opsiyonel: masaüstü girişi ekleyin:

```
echo '[Desktop Entry]
Encoding=UTF-8
Version=4.0
Type=Application
Exec=konsole -e ani-cli
Name=ani-cli' > ~/.local/share/applications/ani-cli.desktop
```
.desktop girişi, ani-cli'nin Konsole'da doğrudan "Oyun Modu "ndan başlatılmasına izin verecektir
Steam Masaüstü uygulamasında:
`Oyun ekle` > `Steam dışı bir oyun ekle` > `ani-cli` için bir kutuyu işaretle > `Seçili programları ekle`
*Not: "Oyun Modu "ndan başlatıldığında Konsole pencere boyutu hata veriyor.*
*Not: Bu henüz olması gerektiği gibi çalışmıyor.*

## Kaldırma

* apt:
```sh
sudo apt remove ani-cli
# to remove the repository from apt
sudo rm -f /etc/apt/trusted.gpg.d/ani-cli.asc /etc/apt/sources.list.d/ani-cli-debian.list
```
* dnf:
```sh
sudo dnf remove ani-cli      # for ani-cli
# disable the repo in dnf
dnf copr disable derisis13/ani-cli
```
Eğer kullanmıyorsanız RPM fusion'ı kaldırmak isteyebilirsiniz
* zypper:
```sh
zypper remove ani-cli
zypper removerepo ani-cli
```
Eğer ihtiyacınız yoksa `packman-essentials`ı kaldırmak isteyebilirsiniz
* AUR:
```sh
yay -R ani-cli
```
* Scoop:
```sh
scoop uninstall ani-cli
```
* Linux:  
```sh
sudo rm "/usr/local/bin/ani-cli"
```
* Mac:  
```sh
rm "$(brew --prefix)/bin/ani-cli"
```
* Windows:
**Git Bash** içinde çalıştırın (yönetici olarak):
```sh
rm "/usr/bin/ani-cli"
```
* Termux paketi
```sh
pkg remove ani-cli
```
* Android:
```sh
rm "$PREFIX/bin/ani-cli"
```
* Steam Deck
```sh
rm "~/.local/bin/ani-cli"
rm -rf ~/.ani-cli
```
isteğe bağlı olarak: bağımlılıkları kaldırın:
```sh
rm ~/.local/bin/aria2c
rm -rf "~/.aria2"
rm -rf "~/.fzf"
flatpak uninstall io.mpv.Mpv
```

## Bağımlılıklar

- grep
- sed
- curl
- mpv - Video Oynatıcı
- iina - MacOS için mpv'nin yerine geçen oynatıcı
- aria2c - İndirme yöneticisi
- ffmpeg - m3u8 İndirici
- fzf - Kullanıcı Arayüzü

## Kankalar

* [animdl](https://github.com/justfoolingaround/animdl): Gülünç derecede verimli, hızlı ve hafif (çoğu kaynağı destekler: allanime, zoro ... (Python)
* [jerry](https://github.com/justchokingaround/jerry): discord presence ile anilist izleme ve senkronizasyon ile anime akışı (Shell)
* [anipy-cli](https://github.com/sdaqo/anipy-cli): ani-cli python ile yeniden yazdı (Python)
* [saikou](https://github.com/saikou-app/saikou): Anilist entegrasyonu ile anime/manga için en iyi android uygulaması (Kotlin)
* [mangal](https://github.com/metafates/mangal): Anilist senkronizasyonu ile herhangi bir kaynaktan manga indirin ve okuyun (Git)
* [lobster](https://github.com/justchokingaround/lobster): Terminalden film ve dizi izleyin (Shell)
* [mov-cli](https://github.com/mov-cli/mov-cli): Cli'de film/şov izleme (Python/Shell)
* [dra-cla](https://github.com/CoolnsX/dra-cla): Kore dizileri için ani-cli eşdeğeri (Shell)
* [redqu](https://github.com/port19x/redqu):  Medya merkezli bir reddit istemcisi (Clojure)
