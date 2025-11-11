[oh-my-zsh] Would you like to update? [Y/n] n
[oh-my-zsh] You can update manually by running `omz update`

 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  git clone git@github.com:AravindSatyan/ML_Ops-hero-Program.git
Cloning into 'ML_Ops-hero-Program'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done.
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  kubectl get nodes
docker ps

NAME             STATUS   ROLES           AGE   VERSION
docker-desktop   Ready    control-plane   49s   v1.32.2
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  # Run Jenkins container (maps docker.sock and your ~/.kube into Jenkins)
docker run -d --name jenkins \
  -p 8080:8080 -p 50000:50000 \
  -v jenkins-data:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v $HOME/.kube:/var/jenkins_home/.kube:ro \
  jenkins/jenkins:lts

Unable to find image 'jenkins/jenkins:lts' locally
lts: Pulling from jenkins/jenkins
cae3b572364a: Pull complete 
11c82e82e8c5: Pull complete 
6d8ebcba18e6: Pull complete 
e29665228ac2: Pull complete 
cc05fa07d253: Pull complete 
7c2b9fc47dae: Pull complete 
9e58f885f660: Pull complete 
51148860bddf: Pull complete 
eba243d676e4: Pull complete 
04e220b291b8: Pull complete 
b9bcce170b58: Pull complete 
606dcc9d6add: Pull complete 
Digest: sha256:f2519b99350faeaaeef30e3b8695cd6261a5d571c859ec37c7ce47e5a241458d
Status: Downloaded newer image for jenkins/jenkins:lts
25ae0b1455061ace9bd3bddfb48baafdb6c06a8524c9d2df35497da836611049
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  docker exec -u root -it jenkins bash -lc '
  curl -L -o /usr/local/bin/kubectl https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl &&
  chmod +x /usr/local/bin/kubectl &&
  kubectl version --client'

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   138  100   138    0     0    765      0 --:--:-- --:--:-- --:--:--   766
100 57.7M  100 57.7M    0     0  17.0M      0  0:00:03  0:00:03 --:--:-- 20.5M
Client Version: v1.34.1
Kustomize Version: v5.7.1

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug jenkins
    Learn more at https://docs.docker.com/go/debug-cli/
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  open http://localhost:8080
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
81faef2fabb74661b9c801d5dbd3a7d5
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
81faef2fabb74661b9c801d5dbd3a7d5
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  docker exec -it jenkins kubectl get ns
NAME              STATUS   AGE
default           Active   6m57s
kube-node-lease   Active   6m57s
kube-public       Active   6m57s
kube-system       Active   6m57s

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug jenkins
    Learn more at https://docs.docker.com/go/debug-cli/
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  kubectl get pods -n data-cleaner
kubectl -n data-cleaner get svc
kubectl -n data-cleaner port-forward svc/data-cleaner 8080:80
curl -s localhost:8080/health
No resources found in data-cleaner namespace.
No resources found in data-cleaner namespace.
Error from server (NotFound): namespaces "data-cleaner" not found
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  kubectl apply -f k8s/namespace.yaml
error: the path "k8s/namespace.yaml" does not exist
 ✘ hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program  ↰ main ±✚  cd
 hariaravi@Haris-MBP  ~  ↰ main ±✚  cd /Users/hariaravi/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main  ld
ld: no object files specified
 ✘ hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main  ls
app         Dockerfile  Jenkinsfile k8s         README.md   tests
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main  kubectl apply -f k8s/namespace.yaml
namespace/data-cleaner created
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main  kubectl -n data-cleaner get pods
kubectl -n data-cleaner port-forward svc/data-cleaner 8080:80
curl -s localhost:8080/health
No resources found in data-cleaner namespace.
Error from server (NotFound): services "data-cleaner" not found
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main  # from your repo root (where Dockerfile lives)
docker build -t data-cleaner:dev .

[+] Building 26.4s (11/11) FINISHED                                                                                             docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                                                            0.0s
 => => transferring dockerfile: 339B                                                                                                            0.0s
 => [internal] load metadata for docker.io/library/python:3.11-slim                                                                             0.7s
 => [internal] load .dockerignore                                                                                                               0.0s
 => => transferring context: 81B                                                                                                                0.0s
 => [1/6] FROM docker.io/library/python:3.11-slim@sha256:e4676722fba839e2e5cdb844a52262b43e90e56dbd55b7ad953ee3615ad7534f                       5.7s
 => => resolve docker.io/library/python:3.11-slim@sha256:e4676722fba839e2e5cdb844a52262b43e90e56dbd55b7ad953ee3615ad7534f                       0.1s
 => => sha256:d7ecded7702a5dbf6d0f79a71edc34b534d08f3051980e2c948fba72db3197fc 29.78MB / 29.78MB                                                0.8s
 => => sha256:1ee9c106547f05aa380c4cdec2837c546439943d73d965a3fc49f228dc8be993 1.29MB / 1.29MB                                                  0.4s
 => => sha256:f002d17b63fe84a7f8a66f20cfa63aec4f6cd2a44069f05b6296b0abfcf2a8e1 14.36MB / 14.36MB                                                0.5s
 => => sha256:e4676722fba839e2e5cdb844a52262b43e90e56dbd55b7ad953ee3615ad7534f 10.37kB / 10.37kB                                                0.0s
 => => sha256:b596083aa14d47c78a652138aa9b98607585499d7c7ec343ae378f6c5770822d 1.75kB / 1.75kB                                                  0.0s
 => => sha256:870925f757415a696459255b0a20b082e914cac42efaff4424b59e21bff80d5b 5.48kB / 5.48kB                                                  0.0s
 => => sha256:65868b001a40155a1d3f5aa7f5a10ba02a7d55697301839dc047c9d549b670bc 248B / 248B                                                      0.5s
 => => extracting sha256:d7ecded7702a5dbf6d0f79a71edc34b534d08f3051980e2c948fba72db3197fc                                                       2.6s
 => => extracting sha256:1ee9c106547f05aa380c4cdec2837c546439943d73d965a3fc49f228dc8be993                                                       0.2s
 => => extracting sha256:f002d17b63fe84a7f8a66f20cfa63aec4f6cd2a44069f05b6296b0abfcf2a8e1                                                       1.6s
 => => extracting sha256:65868b001a40155a1d3f5aa7f5a10ba02a7d55697301839dc047c9d549b670bc                                                       0.0s
 => [internal] load build context                                                                                                               0.0s
 => => transferring context: 1.53kB                                                                                                             0.0s
 => [2/6] WORKDIR /app                                                                                                                          0.4s
 => [3/6] COPY app/requirements.txt .                                                                                                           0.0s
 => [4/6] RUN pip install --no-cache-dir -r requirements.txt                                                                                   17.5s
 => [5/6] COPY app ./app                                                                                                                        0.0s 
 => [6/6] RUN useradd -m runner                                                                                                                 0.2s 
 => exporting to image                                                                                                                          1.5s 
 => => exporting layers                                                                                                                         1.5s
 => => writing image sha256:87fc962f32fec7b37d59e5cc3701445f1bb705a6d3d79bf79d116758ef29c1f6                                                    0.0s
 => => naming to docker.io/library/data-cleaner:dev                                                                                             0.0s

View build details: docker-desktop://dashboard/build/desktop-linux/desktop-linux/qiey6tw1jde8i4zv9xfadm79b

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview 
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main  # 1) Service (creates svc/data-cleaner)
kubectl -n data-cleaner apply -f k8s/service.yaml

# 2) Deployment, but swap the image to your local build on the fly:
sed 's#image: .*#image: data-cleaner:dev#' k8s/deployment.yaml \
| kubectl -n data-cleaner apply -f -

# 3) Wait for rollout
kubectl -n data-cleaner rollout status deployment/data-cleaner --timeout=120s
kubectl -n data-cleaner get pods

service/data-cleaner created
deployment.apps/data-cleaner created
Waiting for deployment "data-cleaner" rollout to finish: 0 of 1 updated replicas are available...
deployment "data-cleaner" successfully rolled out
NAME                            READY   STATUS    RESTARTS   AGE
data-cleaner-7cc65f946f-6tgbd   1/1     Running   0          8s
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main  kubectl -n data-cleaner port-forward svc/data-cleaner 8080:80
# in another terminal:
curl -s localhost:8080/health

Forwarding from 127.0.0.1:8080 -> 8000
Forwarding from [::1]:8080 -> 8000








Handling connection for 8080
Handling connection for 8080
Handling connection for 8080
Handling connection for 8080
Handling connection for 8080
Handling connection for 8080
[1]    95269 terminated  kubectl -n data-cleaner port-forward svc/data-cleaner 8080:80
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main ±  
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main ±  
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main ±  
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main ±  
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main ±  
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main ±  
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main ±  
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main ±  
 hariaravi@Haris-MBP  ~/PycharmProjects/MLOps_hero_Program/ML_Ops-hero-Program   main ±  