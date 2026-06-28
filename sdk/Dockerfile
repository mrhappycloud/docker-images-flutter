FROM ghcr.io/cirruslabs/android-sdk:36

LABEL org.opencontainers.image.source=https://github.com/adrianjagielak/docker-images-flutter
LABEL org.opencontainers.image.description="Flutter SDK on top of the Android SDK. Continued fork of cirruslabs/docker-images-flutter."
LABEL org.opencontainers.image.licenses=MIT

USER root

ARG flutter_version

ENV FLUTTER_HOME=${HOME}/sdks/flutter \
    FLUTTER_VERSION=$flutter_version
ENV FLUTTER_ROOT=$FLUTTER_HOME

ENV PATH=${PATH}:${FLUTTER_HOME}/bin:${FLUTTER_HOME}/bin/cache/dart-sdk/bin

RUN git clone --depth 1 --branch ${FLUTTER_VERSION} https://github.com/flutter/flutter.git ${FLUTTER_HOME}

RUN yes | flutter doctor --android-licenses \
    && flutter doctor \
    && chown -R root:root ${FLUTTER_HOME}

RUN flutter precache --android
RUN sdkmanager "--update" "--verbose"
RUN sdkmanager "ndk;28.0.13004108"
RUN sdkmanager "ndk;27.0.12077973"
RUN sdkmanager "platforms;android-36"
RUN sdkmanager "platforms;android-35"
RUN sdkmanager "platforms;android-34"
RUN sdkmanager "platforms;android-31"
RUN sdkmanager "build-tools;35.0.0"
RUN sdkmanager "cmake;3.22.1"
