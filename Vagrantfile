Vagrant.configure("2") do |config|
  config.vm.box = "almalinux/8"
    config.vm.provision "shell", inline: <<-SHELL
      sudo dnf module enable -y postgresql:13 && sudo dnf install -y postgresql-server postgresql-devel
      sudo postgresql-setup --initdb
      sudo systemctl start postgresql
      sudo systemctl enable postgresql
      sudo mkdir /var/homework && sudo chmod 777 /var/homework


      #2 лекция

      echo "1 задание\n" | sudo tee /var/homework/02_lesson
      sudo -u postgres psql -c '\conninfo' | sudo tee -a /var/homework/02_lesson

      echo -en "\n\n2 задание\n" | sudo tee -a /var/homework/02_lesson
      sudo -u postgres psql -c '\t' -c '\a' -c 'SELECT * FROM pg_tables;' | sudo tee -a /var/homework/02_lesson

      echo -en "\n\n3 задание\n" | sudo tee -a /var/homework/02_lesson
      echo -n "\setenv PAGER 'less -XS'" | sudo tee /var/lib/pgsql/.psqlrc

      echo -en "\n\n4 задание\n" | sudo tee /var/homework/02_lesson
      echo -n "\set PROMPT1 '%#@%/=#'" | sudo tee -a /var/lib/pgsql/.psqlrc
      
      echo -en "\n\n5 задание\n" | sudo tee -a /var/homework/02_lesson
      echo -n "\timing on" | sudo tee -a /var/lib/pgsql/.psqlrc


      #3 лекция

      
    SHELL
end
