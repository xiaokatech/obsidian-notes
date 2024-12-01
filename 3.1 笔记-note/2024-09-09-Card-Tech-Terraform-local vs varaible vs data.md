#Card #Tech #Tech/Terraform

## Context

What
Why
How

## Chat

### terraform local vs variable

Terraform `locals` and `variables` are both used to define reusable values in your Terraform configurations, but they serve different purposes and have distinct characteristics. Here's a comparison:

Terraform Variables:

1. Purpose: Used for accepting input values from outside the configuration.
2. Scope: Can be set at runtime, in a separate file (terraform.tfvars), or via environment variables.
3. Declaration: Declared using the `variable` block.
4. Usage: Referenced using `var.variable_name`.
5. Default values: Can have default values, but are meant to be overridden.
6. Validation: Can have validation rules.
7. Type constraints: Can have type constraints.
8. Use case: Ideal for values that might change between different environments or deployments.

Example:

```hcl
variable "instance_type" {
  type    = string
  default = "t2.micro"
}

resource "aws_instance" "example" {
  instance_type = var.instance_type
}
```

Terraform Locals:

1. Purpose: Used for assigning a name to an expression for reuse within a module.
2. Scope: Only accessible within the module where they are declared.
3. Declaration: Declared using the `locals` block.
4. Usage: Referenced using `local.name`.
5. Default values: Always have a defined value, not meant to be overridden from outside.
6. Validation: No built-in validation (but the expressions must be valid).
7. Type constraints: Inferred from the assigned value.
8. Use case: Ideal for simplifying complex expressions or calculations used multiple times in a configuration.

Example:

```hcl
locals {
  common_tags = {
    Environment = "Production"
    Project     = "MyApp"
  }
}

resource "aws_instance" "example" {
  tags = merge(local.common_tags, {
    Name = "ExampleInstance"
  })
}
```

Key Differences:

1. Input vs. Internal: Variables are for external input, locals are for internal reuse.
2. Mutability: Variables can be changed at runtime, locals are fixed within the configuration.
3. Scope: Variables can be used across modules (if passed), locals are module-specific.
4. Complexity: Locals can hold more complex expressions and calculations.

Choose variables when you need values that might change between deployments or environments. Use locals when you want to simplify your code by reusing complex expressions or calculations within a module.

### terraform data vs variable

Terraform data sources and variables are both used to bring information into your Terraform configuration, but they serve different purposes and have distinct characteristics. Here's a comparison of Terraform data sources and variables:

Terraform Data Sources:

1. Purpose: Used to fetch information from external sources or existing infrastructure.
2. Read-only: Data sources are read-only and cannot be modified within Terraform.
3. Dynamic: Data is fetched at runtime during Terraform operations.
4. External information: Retrieves data from outside the Terraform configuration.
5. Syntax: Defined using the `data` block in Terraform.
6. Examples: AWS AMI IDs, IP ranges, DNS records, etc.

Example:

```hcl
data "aws_ami" "ubuntu" {
  most_recent = true
  owners      = ["099720109477"] # Canonical

  filter {
    name   = "name"
    values = ["ubuntu/images/hvm-ssd/ubuntu-focal-20.04-amd64-server-*"]
  }
}
```

Terraform Variables:

1. Purpose: Used to parameterize your Terraform configuration.
2. Modifiable: Can be set and modified by users when running Terraform.
3. Static: Values are typically set before Terraform operations begin.
4. Internal configuration: Used to make your Terraform code more flexible and reusable.
5. Syntax: Defined using the `variable` block in Terraform.
6. Examples: Instance types, region names, environment names, etc.

Example:

```hcl
variable "instance_type" {
  type    = string
  default = "t2.micro"
}
```

Key Differences:

1. Source of information:

    - Data sources fetch information from external sources.
    - Variables are typically set by users or in variable files.

2. Mutability:

    - Data sources are read-only.
    - Variables can be modified and overridden.

3. Timing:

    - Data sources are queried during Terraform operations.
    - Variables are typically set before Terraform operations begin.

4. Use case:

    - Data sources are used to retrieve existing information.
    - Variables are used to parameterize and customize your configuration.

5. Scope:
    - Data sources are often specific to a provider or resource.
    - Variables can be used throughout your Terraform configuration.

In practice, you might use both data sources and variables in your Terraform configurations. For example, you could use a data source to fetch the latest AMI ID and a variable to specify the instance type when creating an EC2 instance.

## Solution

`locals` and `variables`: locals for internal usage to simplify config and can't be onverrided, variables get values from outside of configuration and can be overridden by inputs.

`data` is for fetch data info from outside of configurayion, and fetch data during terraform operations, `variable` is configured by user inputs and internal configuration, and defined before terraform opoerations.

## Resource

- Template: [[2024-09-10-模板-card-<subject>]]
- Reference: [[What is the general format for citing articles]]
