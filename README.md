<h2 align="center"><b>OpenBoard</b></h2>
<h4 align="center">100% FOSS keyboard, based on AOSP.</h4>
<p align="center"><img src='images/open_board_final.png' height='128'></p>

## Contribute

### Translate OpenBoard
You can help in translating OpenBoard in your language through our [Weblate project](https://hosted.weblate.org/engage/openboard/).
[![Translation status](https://hosted.weblate.org/widgets/openboard/-/openboard/horizontal-blue.svg)](https://hosted.weblate.org/engage/openboard/)

### Create a dictionary
You can use [this tool](https://github.com/remi0s/aosp-dictionary-tools) to create a dictionary. You need a wordlist, as described [here](dictionaries/sample.combined). The output .dict file must be put in [res/raw](app/src/main/res/raw), its wordlist in [dictionnaries](/dictionaries).

For your dictionnary to be merged, you need to provide the wordlist you used, as well as its license if any.

### APK Development

#### Linux

Install java:
```sh
sudo pacman -S jdk11-openjdk jre11-openjdk jre11-openjdk-headless
```

Install Android SDK:
```sh
sudo pacman -S snapd
sudo snap install androidsdk
```

Configure your SDK location in your `~/.bash_profile` or `~/.bashrc`:
```bash
export ANDROID_SDK_ROOT=~/snap/androidsdk/current/AndroidSDK/
```

Compile the project. This will install all dependencies, make sure to accept
licenses when prompted.

```sh
./gradlew assembleDebug
```

Connect your phone and install the debug APK
```sh
adb install ./app/build/outputs/apk/debug/app-debug.apk
```

#### Generate KeyboardTextsTable.java
Make your modifications in [tools/make-keyboard-text/src/main/resources](tools/make-keyboard-text/src/main/resources)/values-YOUR LOCALE.

Generate the new version of [KeyboardTextsTable.java](app/src/main/java/org/dslul/openboard/inputmethod/keyboard/internal/KeyboardTextsTable.java):
```sh
./gradlew tools:make-keyboard-text:makeText
```

## Credits
- Icon by [Marco TLS](https://www.marcotls.eu)
- [AOSP Keyboard](https://android.googlesource.com/platform/packages/inputmethods/LatinIME/)
- [LineageOS](https://review.lineageos.org/admin/repos/LineageOS/android_packages_inputmethods_LatinIME)
- [Simple Keyboard](https://github.com/rkkr/simple-keyboard)
- [Indic Keyboard](https://gitlab.com/indicproject/indic-keyboard)
- Our [contributors](https://github.com/openboard-team/openboard/graphs/contributors)
