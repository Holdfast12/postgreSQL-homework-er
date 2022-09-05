Vagrant.configure("2") do |config|
  config.vm.box = "almalinux/8"
    config.vm.provision "shell", inline: <<-SHELL
      sudo dnf module enable -y postgresql:13 && sudo dnf install -y postgresql-server postgresql-devel postgresql-contrib
      sudo postgresql-setup --initdb
      sudo systemctl start postgresql
      sudo systemctl enable postgresql
      sudo -u postgres psql -c '\t' -c '\a' -c 'CREATE USER vagrant; ALTER USER vagrant SUPERUSER; ALTER USER vagrant CREATEDB;'
      mkdir ./homework/ && chown vagrant:vagrant ./homework/

    #2 лекция
      #1 задание
      echo "1 задание\n" | sudo -u vagrant tee ./homework/02_lesson
      sudo -u vagrant psql postgres -c '\\conninfo' | sudo -u vagrant tee -a ./homework/02_lesson
      #2 задание
      echo -en "\n\n2 задание\n" | sudo -u vagrant tee -a ./homework/02_lesson
      sudo -u vagrant psql postgres -c '\t' -c '\a' -c 'SELECT * FROM pg_tables;' | sudo -u vagrant tee -a ./homework/02_lesson
      #3 задание
      echo -en "\\setenv PAGER 'less -XS'\n" | sudo tee /home/vagrant/.psqlrc
      #4 задание
      echo -en "\\set PROMPT1 '%#@%/=#'\n" | sudo tee -a /home/vagrant/.psqlrc
      #5 задание
      echo -n "\\timing on" | sudo tee -a /home/vagrant/.psqlrc
    #8 лекция
      #создание базы данных в кластере, по умолчанию шаблон template1
      sudo -u vagrant psql postgres -c 'CREATE DATABASE vagrant;'
      #установка расширения на шаблон
      sudo -u vagrant psql template1 -c 'CREATE EXTENSION pgcrypto;'
      sudo -u vagrant psql postgres -c 'CREATE DATABASE db;'
    SHELL
end
