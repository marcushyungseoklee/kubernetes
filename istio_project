[ISTIO 셋팅방법]

1. istio 다운로드
 curl -L https://git.io/getLatestIstio | ISTIO_VERSION=1.1.6 sh -

2. 다운로드 폴더로 이동
 $ cd istio-1.1.6

3. 환경변수 등록
 $ export PATH=$PWD/bin:$PATH

4. Helm Chart repo clone
 helm repo add istio.io https://storage.googleapis.com/istio-release/releases/1.1.6/charts/
 
 
[ISTIO Helm 템플릿으로 설치]

1. istio-system의 컴포넌트 생성
 kubectl create namespace istio-system

2. ISTIO CRD 생성
 helm template install/kubernetes/helm/istio-init --name istio-init --namespace istio-system | kubectl apply -f -

3. 53 istio CRD 검증
 kubectl get crds | grep 'istio.io\|certmanager.k8s.io' | wc -l

4. helm install로 Helm과 Tiller 설치
 kubectl apply -f install/kubernetes/helm/helm-service-account.yaml
 
5. 클러스터에 Tiller 서비스 어카운트 생성
 helm init --service-account tiller
 
 6. istio를 모니터링 서비스와 함께 설치
  helm install install/kubernetes/helm/istio --name istio-init --namespace istio-system --set tracing.enabled=true --set global.mtls.enabled=true
  --set grafana.enabled=true --set kiali.enabled=true --set servicegraph.enabled=true
  
 7. 설치 검증
  1) istio-system 서비스 검증
  kubectl get svc -n istio-system
  
  2) 포드 생성여부 검증
  kubectl get pods -n istio-system
 


 


