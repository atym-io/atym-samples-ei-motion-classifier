# Copyright (C) 2026 Atym, Inc.  All rights reserved.

FROM ghcr.io/atym-io/atym-toolchain/atym-toolchain:latest AS atym-dev

ARG USERNAME=atym-dev
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Accomodate the user for devcontainer
RUN (userdel -r $USERNAME ; userdel -r `id -nu $USER_UID` ; groupdel `id -ng $USER_GID`) || true \
    && groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME -s /bin/bash \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME

WORKDIR /home/$USERNAME
