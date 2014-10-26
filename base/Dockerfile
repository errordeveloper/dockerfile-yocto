# Using base arch development image

FROM base/devel:minimal

RUN pacman --sync --refresh --sysupgrade --noconfirm 
RUN pacman --sync --noconfirm \
	git python2 diffstat chrpath wget cpio sdl

# Dump the list of synced packages so it can be seen
# in Docker hub build output
RUN pacman --query

RUN ln -s /usr/bin/python2 /usr/local/bin/python

# Remove cached package files to keep the image slim
RUN rm /var/cache/pacman/pkg/*

RUN useradd \
	--comment "The mighty freemason robot!" \
	--groups users,wheel,disk,tty \
	--shell /bin/bash \
	--create-home \
	--base-dir / \
	builder

RUN echo '%wheel ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers

ENTRYPOINT [ "/bin/bash" ]
USER builder
ENV HOME /builder

CMD [ "-l" ]
