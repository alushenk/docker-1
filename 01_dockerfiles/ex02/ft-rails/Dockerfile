FROM ruby
# RUN apt update -y && apt install -y build-essential libpq-dev nodejs sqlite3
RUN apt update -y \
    && apt install -y \
    sqlite3 \
    build-essential \
    libpq-dev \
    nodejs

ONBUILD ADD app /opt/app
ONBUILD WORKDIR /opt/app

# ONBUILD RUN bundle update nokogiri
ONBUILD RUN bundle install
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed

# ONBUILD RUN mkdir /opt/app
# ONBUILD WORKDIR /opt/app
# ONBUILD COPY app/Gemfile Gemfile
# ONBUILD COPY app/Gemfile.lock Gemfile.lock
# ONBUILD RUN gem install bundler && bundle install --jobs 20 --retry 5
# # ONBUILD RUN bundle install --full-index
# ONBUILD COPY app /app

# ONBUILD EXPOSE 3000
# ONBUILD RUN rake db:migrate
# ONBUILD RUN rake db:seed