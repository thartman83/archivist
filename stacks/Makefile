ANSIBLE=ansible-playbook
HOSTS=inventory/hosts.ini
EMACS=emacs

tangle: README.org
	${EMACS} $< --batch --eval '(org-babel-tangle-file "README.org")'

provision: tangle
	${ANSIBLE} -i ${HOSTS} provision-redis-server.yml

clean: tangle
	${ANSIBLE} -i ${HOSTS} unprovision-redis-server.yml
