FROM		cydev/cybuntu
MAINTAINER 	Alexandr Razumov ernado@ya.ru
# base for pypy projects
# Python 2.7.3 (87aa9de10f9ca71da9ab4a3d53e0ba176b67d086, Mar 02 2014, 07:55:35)
# [PyPy 2.2.1 with GCC 4.7.3] on linux2
# pypy wth pip

# installing dependencies for pypy compilation
# RUN apt-get install python-dev libffi-dev libsqlite3-dev pkg-config libz-dev libbz2-dev libncurses-dev libexpat1-dev libssl-dev libgc-dev python-sphinx python-greenlet		-y -q
# downloading & extracting pypy
RUN	wget http://24827.selcdn.ru/cydev/pypy-2.2.1.7z -nv
RUN	7z x pypy-2.2.1.7z
# RUN	rm pypy-2.2.1-src.7z
# compiling pypy
# WARNING: may take some time (~1.5 hours or even more), so use it from cache until new pypy version
# RUN	cd pypy-2.2.1-src/pypy/goal && python ../../rpython/bin/rpython --opt=jit targetpypystandalone.py
# replacing python by pypy
RUN rm /usr/bin/python && ln -s /pypy-2.2.1-src/pypy/goal/pypy-c /usr/bin/python
# easy_install
# modifying PATH variable
ENV PATH /pypy-2.2.1-src/bin:$PATH
RUN	wget https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py -nv
RUN	python ez_setup.py
RUN	easy_install pip
ENTRYPOINT 	["python"]
