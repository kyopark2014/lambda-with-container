# Container image를 이용하여 Lambda로 ML inference 구축하기 

It describes how to use container image for lambda deployment in order to use ML algorithms.


```python
FROM public.ecr.aws/lambda/python:3.8

# Copy function code
COPY app.py ${LAMBDA_TASK_ROOT}

# Install the function's dependencies using file requirements.txt
# from your project folder.

COPY requirements.txt .
RUN pip3 install -r requirements.txt —target "${LAMBDA_TASK_ROOT}"

# Set the CMD to your handler (could also be done as a parameter override outside of the Dockerfile)
CMD [ "app.handler" ]
```




## Reference 

[How do I use container images with Lambda?](https://aws.amazon.com/ko/premiumsupport/knowledge-center/lambda-container-images/)

[AWS Lambda의 새로운 기능 — 컨테이너 이미지 지원](https://aws.amazon.com/ko/blogs/korea/new-for-aws-lambda-container-image-support/)

[[AWS Lambda] Container Image 기반 Lambda 함수 구현](https://wooono.tistory.com/337)

[[AWS Lambda] 서버리스 환경에서 ML 추론 작업 수행해보기](https://manchann.tistory.com/42)

[@aws-cdk/aws-ecr module](https://docs.aws.amazon.com/cdk/api/v1/docs/aws-ecr-readme.html)

[class DockerImageFunction (construct)](https://docs.aws.amazon.com/cdk/api/v1/docs/@aws-cdk_aws-lambda.DockerImageFunction.html)
