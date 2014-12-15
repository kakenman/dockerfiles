FROM centos
MAINTAINER kakenman <s.shinya5225@gmail.com>
RUN echo "install ruby environment"
RUN yum install -y git vim sudo tar wget
RUN yum install -y gcc make gcc-c++ zlib-devel httpd-devel openssl-devel curl-devel sqlite-devel

RUN cd /root/ && wget http://cache.ruby-lang.org/pub/ruby/2.1/ruby-2.1.1.tar.gz
RUN cd /root/ && tar zxvf ruby-2.1.1.tar.gz
RUN cd /root/ruby-2.1.1 && ./configure && make && make install
RUN gem install bundler --no-ri --no-rdoc -V
RUN gem install rb-readline --no-ri --no-rdoc -V

RUN echo "Install rails"
RUN gem install rails --no-ri --no-rdoc -V
RUN echo rails -v

RUN git clone https://github.com/kakenman/dummy_rails.git
WORKDIR /dummy_rails
RUN bundle install
EXPOSE 3000
RUN rails s