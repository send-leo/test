# Installing or upgrading eksctl

https://docs.aws.amazon.com/ko_kr/eks/latest/userguide/eksctl.html

- Install the Weaveworks Homebrew tap
```
brew tap weaveworks/tap
```

- Install or upgrade eksctl.
```
exportbrew install weaveworks/tap/eksctl
brew upgrade eksctl && brew link --overwrite eksctl
```

# Clone repositories

- `vier-healthchecker` uses `vier-provisioning`
- You need to clone both repositories to the same path
```
git clone git@github.com:sendbird/vier-provisioning.git
git clone git@github.com:sendbird/vier-healthchecker.git
cd vier-healthchecker
```

# Login and Init project
- Login to AWS with aws-profile
  - Use user profile.
  - Session is valid for 36 hours.
```
./vrt.sh login leo.park
```
- Init project
```
./vrt.sh init_local loadtest
```

# Build image
- Build image
```
./vrt.sh build
```
- Check image
```
./vrt.sh attach
```

# Push image to ECR
- Push image to ECR
```
./eks.sh push
```
- Check ecr consloe
  - https://ap-northeast-2.console.aws.amazon.com/ecr/repositories?region=ap-northeast-2

# Set cluster name
- Set cluster name
```
export EKS_CLUSTER="leo-v000"
```

# Create EKS Cluster

- Create cluster
```
./eks.sh cluster create
```
- Get cluster list
```
./eks.sh cluster get
```
- Get node-group list
```
./eks.sh nodegroup get
```

# Install dashboard 
- Install dashboard 
```
./eks.sh dashboard_install
```
- Connect to the dashboard
```
./eks.sh dashboard_proxy
```

# Upload envs and scripts

- Upload envs and scripts to configMap
```
./eks.sh config_upload
```

# Create pod, deployment

- Create pod
```
./eks.sh pod create small-room-for-video
```
- Create deployment
```
./eks.sh deploy create login 4
```

# Delete EKS Cluster

- Delete cluster
```
./eks.sh cluster delete
```
- Delete node-group
```
./eks.sh nodegroup delete
```
