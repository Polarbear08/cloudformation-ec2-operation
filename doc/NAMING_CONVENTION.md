# 命名規則

## リソースの名称

### 概要

- 以下の規則に従いケバブケースで命名する。
- `AdditionalInfo`を除く各単語は英小文字と数字だけで構成し、1文字目は英小文字とする。
- `AdditionalInfo`を付ける場合は`ResourceCode`のあとにアンダースコアを置き、英小文字と数字とハイフンだけで構成する。

```txt
${ProjectCode}-${EnvCode}-${FunctionCode}-${ServiceCode}-${ResourceCode}_${AdditionalInfo}
```

| 名称            | 説明              | 文字数  | 必須 |
|----------------|------------------|---------|-----|
| ProjectCode    | プロジェクトコード | 3      | Yes  |
| EnvCode        | 環境コード        | 3      | Yes  |
| FunctionCode   | 機能コード         | 3    | Yes  |
| ServiceCode    | AWSサービスコード  | 3       | Yes  |
| ResourceCode   | リソースコード      | 任意    | Yes  |
| AdditionalInfo | その他の情報       | 任意    | No   |

例)

- 開発環境の1台目のEC2インスタンス  

```txt
ceo-dev-wrk-ec2-ins_01
```

- ステージング環境のAZ1aのプライベートサブネット

```txt
ceo-prd-wrk-ec2-subnet_private-1a
```

- 商用環境のVPC

```txt
ceo-prd-nfn-ec2-vpc
```

### 詳細

#### ProjectCode

| Project Name                 | Project Code     |
|------------------------------|------------------|
| cloudformation-ec2-operation | ceo              |

#### EnvCode

| Environment Name | Env Code | Description     |
|------------------|----------|-----------------|
| Production       | prd      | 本番環境         |
| Staging          | stg      | ステージング環境  |
| Development      | dev      | 開発環境         |

#### FunctionCode

| Function Name    | Function Code | Description |
|------------------|---------------|-------------|
| Non-Functional   | nfn           | 非機能      |
| Worker           | wrk           | ワーカー機能 |

#### ServiceCode, ResourceCode

※`Service Code`および`Resource Codeは非公式。

| CloudFormation Resource Code   | Service Code | Resource Code | Description     |
|--------------------------------|--------------|--------------|-----------------|
| AWS::EC2::VPC                  | ec2          | vpc          | Amazon VPC      |
| AWS::EC2::Instance             | ec2          | ins          | EC2 Instance |
| AWS::EC2::InternetGateway      | ec2          | igw          | Internet Gateway |
| AWS::EC2::NatGateway           | ec2          | ngw          | NAT Gateway |
| AWS::EC2::NetworkInterface     | ec2          | eni          | Network Interface |
| AWS::EC2::NetworkInterfaceAttachment | ec2    | eniattac     | Network Interface Attachment |
| AWS::EC2::Route                | ec2          | route        | Route Table Entry |
| AWS::EC2::RouteTable           | ec2          | rtb          | Route Table |
| AWS::EC2::SecurityGroup        | ec2          | sg           | Security Group  |
| AWS::EC2::SecurityGroupIngress | ec2          | sgri         | Security Group Rule Ingress |
| AWS::EC2::SecurityGroupEgress  | ec2          | sgre         | Security Group Rule egress |
| AWS::EC2::Subnet               | ec2          | subnet       | Subnet          |
| AWS::EC2::SubnetRouteTableAssociation | ec2   | srassoc      | Subnet RouteTable Association |

#### Additional Info

`Resource Code` までで一意に識別できない場合、必要に応じて記載する。

## CloudFormationの論理ID

### 概要

- リソースの名称から`EnvCode`を除いてパスカルケースにしたものにする。
- `AdditionalInfo`については、アンダースコアは残して`AdditionalInfo`の情報自体はパスカルケースにする。

例)

- 開発環境の1台目のEC2インスタンス  

```txt
CeoWrkEc2Ins_01
```

- ステージング環境のAZ1aのプライベートサブネット

```txt
CeoWrkEc2Subnet_Private1a
```

- 商用環境のVPC

```txt
CeoNfnEc2Vpc
```
