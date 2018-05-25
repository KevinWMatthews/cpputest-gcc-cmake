FROM kevinwmatthews/docker-cmake:3.5.1-latest

RUN cd \
    && git clone https://github.com/cpputest/cpputest.git \
    && cd cpputest/cpputest_build \
    && git checkout 2b45d38c5c3dd71447bfe0ae993786a6da898658 \
    && cmake -DC++11=ON -DTESTS=OFF .. \
    && make && make install \
    && rm -rf cpputest
