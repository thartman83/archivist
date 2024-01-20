ANSIBLE=ansible-playbook
DOCKERBUILD=docker build
DOCKERPUSH=docker push
DOCKERREPO=172.17.1.62:5000
IMGNAME=descry
DOCKERVERSION=latest
HOSTS= inventory/hosts.ini
EMACS= emacs
TANGLEFILE=descry.org

tangle: ${TANGLEFILE}
	${EMACS} $< --batch --eval '(org-babel-tangle-file "${TANGLEFILE}")'

docker-image: tangle
	 ${DOCKERBUILD} ~/projects/archivist-descry/. -t ${DOCKERREPO}/${IMGNAME}:${DOCKERVERSION}
	 ${DOCKERPUSH} ${DOCKERREPO}/${IMGNAME}:${DOCKERVERSION}

redeploy: docker-image
	${ANSIBLE} -i inventory/hosts.ini undeploy-descry.yml
	${ANSIBLE} -i inventory/hosts.ini deploy-descry.yml

deploy: Dockerfile
	${ANSIBLE} -i inventory/hosts.ini deploy-descry.yml

undeploy: Dockerfile
	${ANSIBLE} -i inventory/hosts.ini undeploy-descry.yml
