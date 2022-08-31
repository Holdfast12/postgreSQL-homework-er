Vagrant.configure("2") do |config|
  config.vm.box = "almalinux/8"
    config.vm.provision "shell", inline: <<-SHELL
      sudo dnf module enable -y postgresql:13 && sudo dnf install -y postgresql-server postgresql-devel
      sudo postgresql-setup --initdb
      sudo systemctl start postgresql
      sudo systemctl enable postgresql
	  sudo -u postgres psql -c '\t' -c '\a' -c 'CREATE USER vagrant;'
	  sudo -u postgres psql -c '\t' -c '\a' -c 'ALTER USER vagrant SUPERUSER;'
	  mkdir ./homework/ && chown vagrant:vagrant ./homework/

    #2 лекция
      #1 задание
      echo "1 задание\n" | sudo -u vagrant tee ./homework/02_lesson
      sudo -u vagrant psql postgres -c '\\conninfo' | sudo -u vagrant tee -a ./homework/02_lesson
      #2 задание
      echo -en "\n\n2 задание\n" | sudo -u vagrant tee -a ./homework/02_lesson
      sudo -u vagrant psql postgres -c '\t' -c '\a' -c 'SELECT * FROM pg_tables;' | sudo -u vagrant tee -a ./homework/02_lesson
      #3 задание
      echo -n "\\setenv PAGER 'less -XS'" | sudo tee /var/lib/pgsql/.psqlrc
      #4 задание
      echo -n "\\set PROMPT1 '%#@%/=#'" | sudo tee -a /var/lib/pgsql/.psqlrc
      #5 задание
      echo -n "\\timing on" | sudo tee -a /var/lib/pgsql/.psqlrc


    #3 лекция

      
    SHELL
end
