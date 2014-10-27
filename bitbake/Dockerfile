FROM errordeveloper/devenv-yocto:with_cached_repos

RUN git clone --quiet --single-branch --branch daisy --reference repos/poky.git git://git.yoctoproject.org/poky

WORKDIR /builder/poky

ENTRYPOINT [ "/bin/bash", "-x", "-c", "env; run_args=\"$@\"; shift $#; source oe-init-build-env; exec bitbake ${run_args}", "--" ]

CMD [ "core-image-minimal" ]
