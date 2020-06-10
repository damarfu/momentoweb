# Comandos de terminal para el Mac
#ayuda/técnico 
## Desactivar las copias “time Machine” locales del portátil
[Faq-Mac (fuente)](http://www.faq-mac.com/2017/02/desactivar-las-copia-de-seguridad-locales-de-time-machine-en-portatiles/)
*Ha dejado de funcionar en High Sierra para adelante*  
Para ello abre el Terminal y usa el comando:  
sudo tmutil disablelocal  
para reactivarlas usa:  
sudo tmutil enablelocal  
Para determinar su tamaño podemos usar el comando:  
sudo du -h /.MobileBackups/  
y para eliminarla:  
sudo rm -rfv /.MobileBackups/  
A veces está dentro de la carpeta /Volumes/.MobileBackup o un nombre extraño (mira dentro)
- - - -
## Cambiar la extensión y la localización de las Capturas de Pantalla
- Cambiar la extensión
defaults write com.apple.screencapture type jpg
killall SystemUIServer
- Cambiar la ubicación, cambia /Pictures por el directorio que quieras.
defaults write com.apple.screencapture location ~/Pictures
killall SystemUIServer
- - - -
## Activar el modo dark-mode en High Sierra
Activar:
defaults write -g NSWindowDarkChocolate -bool TRUE
Sal de tu usuario y vuelve a entrar
Desactivar:
defaults write -g NSWindowDarkChocolate -bool FALSE
Reinicia el Mac
- - - -
## Ejecutar un Applescript 
$osascript applescript.scpt
- - - -
## Instalador de Brew para Terminal. Instalas paquetes desde terminal
### Instalar HomeBrew
[HomeBrew WEB](https://brew.sh/)
``` 
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

```

### Brew Cask
Ayuda en: [Snazzy Labs](https://pastebin.com/jV9XzPrs) También en su canal de YouTube
$brew cask
Instala paquetes y programas desde la linea de comandos. Útil para programas multiplataforma
[En Github](https://github.com/Homebrew/homebrew-cask/blob/master/USAGE.md)

Instalar paquete
$brew cask Install <paquete>

Lo he usado para instalar los Quicklook Vista rápida de algunas extensiones que no se veían.
[En Githup](https://github.com/sindresorhus/quick-look-plugins/blob/master/readme.md)
#### Activar vista previa de WebP
brew cask install WebPQuickLook
#### Ver la velocidad de internet
 **SPEEDTEST**
	1. //Install Speedtest         brew install speedtest-cli
	2. Run:                        speedtest-cli




### Activar selección de texto en la vista previa
``` c
defaults write com.apple.finder QLEnableTextSelection -bool true; killall Finder
```

Cambia a: false para desactivar
[Fuente](https://coderwall.com/p/94rlia/copy-text-code-from-osx-quicklook-directly)

- - - -
### Mostrar archivos ocultos.
``` 
>defaults write com.apple.Finder AppleShowAllFiles TRUE
>KillAll Finder
# Restablecerlo 
>defaults write com.apple.Finder AppleShowAllFiles FALSE
>KillAll Finder
```

### Enable Trim
``` 
sudo trimforce enable
```

## Terminal configuración del PROMPT de zsh
[Web de ayuda](https://scriptingosx.com/2019/07/moving-to-zsh-06-customizing-the-zsh-prompt/) [Fichero de configuración en español](https://gist.github.com/3rn3st0/c51af47b73927479953e)
Desde Catalina Apple ha cambiado el interprete de comandos de “bash” a “zsh” .
El prompt no me gusta y lo puedes cambiar 
Crear en el directorio del usuario un fichero .zshrc y poner esto 
``` 
#alias
alias ll='ls -al'

#PROMPT
PROMPT='%(?.%F{green}√.%F{red}?%?)%f %B%F{122}%1~%f%b · %B%F{208}%n%f%b %(!.#.>) '
```