FROM errordeveloper/devenv-yocto:with_cached_repos

ENV MACHINE beaglebone

RUN git clone --single-branch --branch daisy --reference repos/poky.git git://git.yoctoproject.org/poky

WORKDIR /builder/poky

ENTRYPOINT [ "/bin/bash", "-x", "-c", "env; source oe-init-build-env; exec bitbake $@", "--" ]

CMD [ "core-image-minimal" ]
