FROM openjdk:8-jdk

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update -qq && apt-get install -qq --no-install-recommends nodejs yarn maven \
&& rm -rf /var/lib/apt/lists/*

RUN git clone --depth=1 https://github.com/yamcs/yamcs /src/yamcs \
&& cd /src/yamcs/yamcs-web && yarn install && yarn build \
&& cd /src/yamcs && mvn package -DskipTests

RUN cd /src/yamcs && ./make-live-devel.sh --yss /yamcs

WORKDIR /yamcs/bin
CMD ./yamcsd
