FROM kevinwmatthews/docker-cmake:3.5.1-latest

RUN cd \
    && git clone https://github.com/cpputest/cpputest.git \
    && cd cpputest/cpputest_build \
    && git checkout v3.8 \
    && cmake -DC++11=ON -DTESTS=OFF .. \
    && make && make install \
    && rm -rf cpputest
