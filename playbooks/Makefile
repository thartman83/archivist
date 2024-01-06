ANSIBLE= ansible-playbook
HOSTS= inventory/hosts.ini
EMACS= emacs

.PHONY: tangle descry

tangle: README.org
	${EMACS} $< --batch --eval '(org-babel-tangle-file "README.org")'

descry: tangle
	${ANSIBLE} -i ${HOSTS} deploy-descry.yml

stacks: tangle
	${ANSIBLE} -i ${HOSTS} deploy-stacks.yml

stacks-app: tangle
	${ANSIBLE} -i ${HOSTS} redeploy-stacks-app.yml
