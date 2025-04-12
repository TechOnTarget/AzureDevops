FROM ubuntu:22.04


# Install required packages
RUN apt-get update && apt-get install -y \
   openjdk-11-jdk \
   wget \
   unzip \
   git \
   curl \
   && apt-get clean


# Install Node.js 16 and npm
RUN curl -fsSL https://deb.nodesource.com/setup_16.x | bash - && \
   apt-get install -y nodejs


# Set environment variables for Android SDK
ENV ANDROID_SDK_ROOT=/opt/android-sdk
ENV PATH=$ANDROID_SDK_ROOT/cmdline-tools/latest/bin:$ANDROID_SDK_ROOT/platform-tools:$PATH


# Install Android Command-line tools
RUN mkdir -p $ANDROID_SDK_ROOT/cmdline-tools && \
   wget -q https://dl.google.com/android/repository/commandlinetools-linux-9477386_latest.zip -O /tmp/tools.zip && \
   unzip /tmp/tools.zip -d $ANDROID_SDK_ROOT/cmdline-tools/ && \
   mv $ANDROID_SDK_ROOT/cmdline-tools/cmdline-tools  $ANDROID_SDK_ROOT/cmdline-tools/latest && \
   rm /tmp/tools.zip


# Accept licenses
RUN yes | sdkmanager --licenses


# Install Android SDK components
#RUN sdkmanager "platform-tools" "platforms;android-31" "build-tools;31.0.0"


WORKDIR /workspace

