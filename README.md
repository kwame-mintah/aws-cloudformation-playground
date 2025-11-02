# 🛝 AWS CloudFormation Playground

As the name of the repository suggests, it's just a [_playground_](https://dictionary.cambridge.org/dictionary/english/playground).
Will be used to store various [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) stack templates for deploying
and configuring various resources.

## Development

The following tools are quite helpful when developing locally, [`cfn-lint`](https://github.com/aws-cloudformation/cfn-lint) for linting CloudFormation files and
[LocalStack](https://www.localstack.cloud/) for testing resource deployment locally, also see [aws-localstack-playground](https://github.com/kwame-mintah/aws-localstack-playground/) providing example(s).

- [cfn-lint-visual-studio-code](https://github.com/aws-cloudformation/cfn-lint-visual-studio-code): CloudFormation Linter IDE integration, autocompletion, and documentation
- [LocalStack](https://github.com/localstack/localstack): A fully functional local AWS cloud stack. Develop and test your cloud & Serverless apps offline

## Example Usages

### Terraform

Below is an example of using the [dynamodb-terraform-deployment-template](dynamodb-terraform-deployment-template.yaml) in Terraform, taken from my [
terraform-aws-certified-devops-engineer-professional
](https://github.com/kwame-mintah/terraform-aws-certified-devops-engineer-professional/blob/56865aa65630b2d2955d74e42b5bdb52ed601b96/cloudformation.tf#L4-L34) repository.

```terraform
data "http" "km_dynamodb_template" {
  request_headers = {
    Accept = "text/yaml"
  }
  url = "https://raw.githubusercontent.com/kwame-mintah/aws-cloudformation-playground/914947c16eafc4bc4ea61f33004ba4671864dc49/dynamodb-terraform-deployment-template.yaml"
}

resource "aws_cloudformation_stack" "dynamodb_table_stack" {
  name               = "${local.name_prefix}-dynamodb-table-stack"
  timeout_in_minutes = 10

  parameters = {
    DynamoDBTableName = "${local.name_prefix}-dynamodb-table"
  }
  template_body = data.http.km_dynamodb_template.response_body

  tags = merge(
    var.tags
    , {
      git_commit           = "a41e271d4cd1ad02a33a66c047b4241304cf0e69"
      git_file             = "cloudformation.tf"
      git_last_modified_at = "2025-04-30 21:19:26"
      git_last_modified_by = "kwame_mintah@hotmail.co.uk"
      git_modifiers        = "kwame_mintah"
      git_org              = "kwame-mintah"
      git_repo             = "terraform-aws-certified-devops-engineer-professional"
      yor_name             = "dynamodb_table_stack"
      yor_trace            = "61ad9e64-d68c-4b31-a2ce-5d48ca47f1c8"
  })
}
```

<!----
Note to self, can override the schema recognised using the following snippet at the top of the YAML
# yaml-language-server: $schema=https://raw.githubusercontent.com/aws-cloudformation/cfn-lint-visual-studio-code/cb52cac9d9d2204a4313f16305f0a6842414e2ca/schema/all-spec.json
----!>
