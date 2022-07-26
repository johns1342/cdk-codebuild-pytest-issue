# repo to demo the AWS CodeBuild/CDK issue

```bash
git clone https://github.com/johns1342/cdk-codebuild-pytest-issue
cd cdk-codebulid-pytest-issue
docker pull public.ecr.aws/codebuild/local-builds:latest
docker pull public.ecr.aws/codebuild/amazonlinux2-x86_64-standard:3.0
curl https://raw.githubusercontent.com/aws/aws-codebuild-docker-images/master/local_builds/codebuild_build.sh > ./codebuild_build.sh
chmod +x codebuild_build.sh
./codebuild_build.sh -i public.ecr.aws/codebuild/amazonlinux2-x86_64-standard:3.0 -a cb_output -m -d
```

After that, the last line you should see before it hangs is:

```early skip of rewriting module: aws_cdk.cloud_assembly_schema._jsii [assertion]```

To make the test work, just comment out the import of `aws_cdk.core` in `tests/test_issue.py`.

