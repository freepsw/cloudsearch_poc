# cloudsearch_poc
Deploy elasticsearch clusters using rancher, ansible

## AWS Cloudsearch와 유사한 서비스 구성 
- 동적으로 elasticsearch cluster를 구성하고 kibana, elastichq등을 배포할 수 있도록 하는 서비스 구성
- Container 기반으로 구성되었으며, container orchestration은 rancher활용하여 전체 container기반 서비스 구성

## Cloudsearch.scripts
- ansible을 활용하여 elasticsearch 클러스터를 동적으로 생성하기 위한 스크립트를 구성함. 
- ansible에서 rancher를 통해서 es cluster 생성에 필요한 container 요청을 실행함. 

## ES 관련 conatiner images들
- oss 이미지를 기준으로 생성
- elasticsearch
- kibana
- elasitchq
