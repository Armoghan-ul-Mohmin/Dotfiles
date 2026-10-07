FROM archlinux:latest

# ─────────────────────────────────────────────
# Configure Arch mirror
# ─────────────────────────────────────────────
RUN printf '%s\n' \
    'Server = https://stable-mirror.omarchy.org/$repo/os/$arch' \
    > /etc/pacman.d/mirrorlist


# ─────────────────────────────────────────────
# Update system and install packages
# ─────────────────────────────────────────────
RUN pacman -Syu --noconfirm \
    base-devel \
    git \
    sudo \
    bash \
    zsh \
    vim \
    neovim \
    curl \
    wget \
    gum \
    bat \
    fzf

# ─────────────────────────────────────────────
# Create dotfiles user
# ─────────────────────────────────────────────
RUN useradd \
    --create-home \
    --shell /bin/bash \
    dotfiles

# ─────────────────────────────────────────────
# Configure sudo
# ─────────────────────────────────────────────
RUN echo "dotfiles ALL=(ALL) NOPASSWD: ALL" \
    > /etc/sudoers.d/dotfiles \
    && chmod 0440 /etc/sudoers.d/dotfiles

# ─────────────────────────────────────────────
# Switch to dotfiles user
# ─────────────────────────────────────────────
USER dotfiles

WORKDIR /home/dotfiles

# ─────────────────────────────────────────────
# Install yay
# ─────────────────────────────────────────────
RUN git clone \
        https://aur.archlinux.org/yay.git \
        /tmp/yay \
    && cd /tmp/yay \
    && makepkg -si --noconfirm \
    && rm -rf /tmp/yay





