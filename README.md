# Fremote 📺
Fremote is an open-source CLI application used to convert instances of Safari and Chrome into wireless remote controls for a host device. This application was created so that I can control my 32" monitor from my bed (about 6ft away), like a TV.

## Installation 📁
There are two recommended methods of installation:
* Cloning this repository.
* Downloading the [.exe file](https://www.dropbox.com/scl/fo/dagkablwswvxfxw7idubl/h?rlkey=bmi7f7ysllwfjvw2y5te8cvx9&dl=0).

### Installation via cloning
To clone this repository from GitHub CLI, enter the following commands into your terminal:
```
gh repo clone JustKindaDoIt/Fremote
npm install
node index.js
```
For convenience, the codebase can then be build as an .exe file with [Nexe](https://github.com/nexe/nexe) via:
`npm run build`

### Installation via download
To install the program via download simply go to this [Dropbox](https://www.dropbox.com/scl/fo/dagkablwswvxfxw7idubl/h?rlkey=bmi7f7ysllwfjvw2y5te8cvx9&dl=0) folder and download the .exe file. This method of installation is currently **windows only**.

## Controls 🎛
The 'remote' (the device that has connected to the host) can currently
* Move the host cursor
  * To move the host cursor, simply move the client cursor or place your finger on the client screen.
  * The client position is then mapped to the host screen.
  * This control is not relative like a mouse and can take getting used to, but is far faster than relative control on larger screens.
* Type and enter key inputs
  * To type on the host device, simply extend the URL of the remote with the string you wish to type.
  * E.g. if I want to type `Brackeys`, I will update the URL on the remote browers to now be `96.84.220.93:3000/Brackeys` or for you `IP:PORT/Brackeys`.
  * To enter a backspace append `/d` to the URL, as in `96.84.220.93:3000/d` or for you `IP:PORT/d`.
* Scroll
  * To scroll up, extend the URL with `/+` or `/n`.
  * E.g. `96.84.220.93:3000/+`.
  * To scroll down, extend the URL with `/-`.
  * E.g. `96.84.220.93:3000/-`.

## Composition 🔎
### Back-end
The app is written in the NodeJS environment. Once the user navigates through the CLI, which is written with [Clack](https://github.com/natemoo-re/clack), a Node server is created on the host device with [Express](https://expressjs.com). The Express library manages GET and USE requests. XTTPS sent to the server is interpretted through USE. This data is then parsed to an [automation library](https://nutjs.dev) where the position of the client cursor is projected to the host and the cursor is moved.
### Front-end
The user interface is an HTML5 document served to any device that connects to the host. The interface is minimal but is sending the live position of the cursor via XTTP every time the cursor is moved.

## Security ⚠️
Fremote makes no attempts to secure ports it opens or encrypt data that is sent through those ports. The application is for education purposes only and intended to be used on a trusted WiFi network and should not be used in public.
