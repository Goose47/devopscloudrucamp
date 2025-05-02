.PHONY: gen, deploy

gen:
	@source .env && \
	kubectl create secret docker-registry docker-registry-credentials \
	--docker-server=https://index.docker.io/v1/ \
	--docker-username=$$DOCKER_REGISTRY_USER \
	--docker-password=$$DOCKER_REGISTRY_PASS \
	--docker-email=your-email \
	--namespace=echo-server \
	--dry-run=client -o yaml > docker-registry-secret.yaml

deploy:
	@kubectl apply -f namespace.yaml && \
    kubectl apply -f docker-registry-secret && \
    kubectl apply -f deployment.yaml && \
    kubectl apply -f service.yaml