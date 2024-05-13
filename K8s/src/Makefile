all: vagrant_down vagrant_up

docker_compose_up:
	docker compose up

vagrant_up:
	vagrant up --provision-with=shell

vagrant_down:
	vagrant halt
	vagrant destroy -f

reload:
	vagrant reload

.PHONY: connect
connect:
ifndef vm
	$(error vm is not set. Usage: make connect vm=1)
endif
	vagrant ssh $(vm)

.PHONY: config
config:
ifndef vm
	vagrant ssh-config
else
	vagrant ssh-config $(vm)
endif

.PHONY: save
save:
ifndef vm
	vagrant snapshot save vm1 latest
	vagrant snapshot save vm2 latest
	vagrant snapshot save vm3 latest
else
	vagrant snapshot save vm$(vm) latest
endif

.PHONY: restore
restore:
ifndef vm
	vagrant snapshot restore vm1 latest
	vagrant snapshot restore vm2 latest
	vagrant snapshot restore vm3 latest
else
	vagrant snapshot restore vm$(vm) latest
endif


