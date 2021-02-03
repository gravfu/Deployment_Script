FROM jenkins/jenkins:lts
USER root
RUN apt-get update && apt-get install -y build-essential cmake
RUN git clone --branch=master --depth 1 https://github.com/Snaipe/Criterion \
  && cd Criterion \
  && mkdir build \
  && cd build \
  && cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo \
           -DCMAKE_INSTALL_PREFIX=/usr \
           -DCMAKE_INSTALL_LIBDIR=lib \
           .. \
  && make \
  && make install \
  && cd ../../ \
  && rm -rf Criterion
USER jenkins
RUN /usr/local/bin/install-plugins.sh cloudbees-folder configuration-as-code credentials github job-dsl script-security structs role-strategy ws-cleanup xml-job-to-job-dsl
