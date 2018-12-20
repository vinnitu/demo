FROM node:10

RUN git clone --depth=1 https://github.com/nasa/openmct-tutorial.git \
&& cd openmct-tutorial \
&& npm install \
&& npm install yamcs-openmct-plugin cors --save \
&& cd node_modules/openmct \
&& npm install \
&& node ./node_modules/bower/bin/bower --allow-root install \
&& node ./node_modules/gulp/bin/gulp.js install

WORKDIR /openmct-tutorial

CMD npm start

