FROM debian:sid

# Deps
RUN echo "deb-src http://ftp.fr.debian.org/debian/ sid main" >> /etc/apt/sources.list
RUN apt-get update -y
RUN apt-get install -y git meson ninja-build sudo
RUN apt-get build-dep -y libretro-gtk0 gnome-games-app

# Don't do everything as root
RUN useradd -m -s /bin/bash --groups sudo toto 
RUN echo "toto ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/toto && \
    chmod 0440 /etc/sudoers.d/toto
USER toto

# libmanette
WORKDIR /tmp
RUN git clone https://gitlab.gnome.org/aplazas/libmanette.git
WORKDIR /tmp/libmanette
RUN meson build && sudo ninja -C build install

# retro-gtk
WORKDIR /tmp
RUN git clone https://github.com/GNOME/retro-gtk
WORKDIR /tmp/retro-gtk
RUN git checkout 738f4d6e1ac090e6d744a39be426ce069bc3716f
RUN meson build && sudo ninja -C build install

# gnome-games
WORKDIR /tmp
RUN git clone git://git.gnome.org/gnome-games
WORKDIR /tmp/gnome-games
RUN ./autogen.sh && ./configure && sudo make install

# Let's go!
ENV LD_LIBRARY_PATH=/usr/local/lib/x86_64-linux-gnu
CMD gnome-games
