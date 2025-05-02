.PHONY: gen, deploy

gen:
	@bash -c 'source .env && \
	kubectl create secret docker-registry docker-registry-credentials \
	--docker-server=https://index.docker.io/v1/ \
	--docker-username=$$DOCKER_REGISTRY_USER \
	--docker-password=$$DOCKER_REGISTRY_PASS \
	--docker-email=your-email \
	--namespace=echo-server \
	--dry-run=client -o yaml > docker-registry-secret.yml'

deploy:
	@kubectl apply -f namespace.yml && \
    kubectl apply -f docker-registry-secret.yml && \
    kubectl apply -f deployment.yml && \
    kubectl apply -f service.yml && \
    kubectl apply -f ingress.yml && \
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.9.5/deploy/static/provider/cloud/deploy.yaml
