ARG BUILD_FROM
FROM $BUILD_FROM AS BUILD

ENV LANG C.UTF-8

RUN apk add --no-cache \
	git=2.26.2-r0 \
	npm=12.20.1-r0 \
	python3=3.8.5-r0 \
	pkgconf=1.7.2-r0 \
	pixman-dev=0.40.0-r2 \
	cairo-dev=1.16.0-r2 \
	pango-dev=1.44.7-r2 \
	build-base=0.5-r2 \
	libjpeg-turbo-dev=2.0.5-r0

RUN git clone https://github.com/groth-its/ICantBelieveItsNotValetudo.git -b base64-inflate /app

WORKDIR /app
RUN npm install


FROM $BUILD_FROM AS RUNNING

RUN apk add --no-cache npm=12.20.1-r0 \
    pixman=0.40.0-r2 \
	cairo=1.16.0-r2 \
	pango=1.44.7-r2 \
	libjpeg-turbo=2.0.5-r0

WORKDIR /app

COPY --from=BUILD /app /app

COPY root /
