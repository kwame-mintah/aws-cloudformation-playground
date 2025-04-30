# 🛝 AWS CloudFormation Playground

As the name of the repository suggests, it's just a [_playground_](https://dictionary.cambridge.org/dictionary/english/playground).
Will be used to store various [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) stack templates for deploying
and configuring various resources.

## Development

The following tools are quite helpful when developing locally, [`cfn-lint`](https://github.com/aws-cloudformation/cfn-lint) for linting CloudFormation files and
[LocalStack](https://www.localstack.cloud/) for testing resource deployment locally, also see [aws-localstack-playground](https://github.com/kwame-mintah/aws-localstack-playground/) providing example(s).

- [cfn-lint-visual-studio-code](https://github.com/aws-cloudformation/cfn-lint-visual-studio-code): CloudFormation Linter IDE integration, autocompletion, and documentation
- [LocalStack](https://github.com/localstack/localstack): A fully functional local AWS cloud stack. Develop and test your cloud & Serverless apps offline

<!----
Note to self, can override the schema recognised using the following snippet at the top of the YAML
# yaml-language-server: $schema=https://raw.githubusercontent.com/aws-cloudformation/cfn-lint-visual-studio-code/cb52cac9d9d2204a4313f16305f0a6842414e2ca/schema/all-spec.json
----!>
