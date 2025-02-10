# Spek

Spek is an acoustic spectrum analyser written in C++. It uses FFmpeg
libraries for audio decoding and wxWidgets for the GUI.

### I have added a frequency reference for different audio file types in the About section of the software.

# Guide to building on Windows
## 1.
I will be using WSL. Clone this repo to ~/
```bash
git clone https://github.com/Mustaali256/spek.git
```
Now install these prerequisites:
```
sudo apt update && sudo apt upgrade -y
sudo apt install libssl-dev make autoconf automake mingw-w64
```
Clone [MXE](https://github.com/mxe/mxe.git) to ~  too then cd into the directory:
```bash
git clone https://github.com/mxe/mxe.git
cd mxe/
```
Then add MXE to PATH by going into ~/.bashrc (or ~/.zshrc) by adding this line into the file:
```bash
export PATH=~/mxe/usr/bin:$PATH
```
Then you want to run this in ~/mxe:
```bash
make pthreads ffmpeg wxwidgets -j$(nproc) MXE_TARGETS='x86_64-w64-mingw32.static'
```

## 2.
Next, run this:
```bash
cd ~/spek/
chmod +x dist/win/bundle.sh autogen.sh
./dist/win/bundle.sh
```

After it has been compiled, you will find the spek.zip in the dist/win/ directory, this is your binary.

# Guide to building on GNU Linux

On Linux it is much simpler.

Clone the repository, configure and make:
```bash
git clone https://github.com/Mustaali256/spek.git
cd spek/
./configure
make -j$(nproc)
```
Your spek binary will be in src/
