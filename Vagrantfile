# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  # 자신의 base box를 지정합니다
  config.vm.box = "centos63-base"

  # base box의 url을 적어놓으면, 이 파일을 공유할 때 다른 사람이 동일한 base box를 다운받을 수 있습니다
  config.vm.box_url = "https://dl.dropbox.com/u/7225008/Vagrant/CentOS-6.3-x86_64-minimal.box"

  # VirtualBox의 폴더 공유 기능을 이용해 Host와 Guest 간에 폴더를 공유합니다
  config.vm.share_folder "v-data", "/vagrant_data", "vagrant_data"

  # Guest Box의 80번 포트를 Host Box의 8080 포트로 forward합니다
  config.vm.forward_port 80, 8080

  # VirtualBox의 메모리 사용량을 512MB로 변경합니다
  config.vm.customize ["modifyvm", :id, "--memory", 512]

  # Chef를 이용해 필요한 패키지를 설치합니다
  config.vm.provision :chef_solo do |chef|
    # Chef는 cookbook이라는 패키지를 통해 패키지 설치 과정을 정의합니다
    # cookbook은 미리 다운받아놓고 디렉토리를 지정할 수도 있고, tar.gz 파일로 업로드해두고 url을 지정할 수도 있습니다
    chef.cookbooks_path = "cookbooks"

    # Guest에 git을 설치합니다
    chef.add_recipe "git"

    # Guest에 erlang을 설치합니다
    chef.add_recipe "erlang"
  end
end
