---
title: 계약 중심 도구
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 1896a76892c76fb7277c3e36978604a4d290018e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255132"
---
# <a name="contract-first-tool"></a>계약 중심 도구

서비스 계약을 기존 서비스에서 만들어야 할 경우가 있습니다. .NET Framework 4.5 이상에서 계약 중심 도구를 사용 하 여 기존 서비스에서 자동으로 데이터 계약 클래스를 만들 수 있습니다. 계약 중심 도구를 사용하려면 XSD(XML 스키마 정의) 파일을 로컬에서 다운로드해야 합니다. 이 도구는 HTTP를 통해 원격 데이터 계약을 가져올 수 없습니다.

 계약 중심 도구는 Visual Studio 2012에 빌드 작업으로 통합 됩니다. 빌드 작업에서 생성하는 코드 파일은 프로젝트가 빌드될 때마다 생성되므로 프로젝트는 기본 서비스 계약에서 변경 사항을 쉽게 채택할 수 있습니다.

 계약 중심 도구가 가져올 수 있는 스키마 유형에는 다음이 포함됩니다.

```xml
<xsd:complexType>
 <xsd:simpleType>
 </xsd:simpleType>
</xsd:complexType>
```

 단순 유형이 `Int16` 또는 `String`과 같은 기본 형식인 경우 생성되지 않으며 복합 형식이 `Collection` 유형의 일부인 경우 생성되지 않습니다. 유형이 다른 `xsd:complexType`의 일부인 경우에도 생성되지 않습니다. 이러한 모든 경우 프로젝트의 기존 유형에 대한 유형이 대신 참조됩니다.

## <a name="adding-a-data-contract-to-a-project"></a>프로젝트에 데이터 계약 추가

 서비스 계약(XSD)이 프로젝트에 추가되어야 계약 중심 도구를 사용할 수 있습니다. 이 개요에서는 다음 계약이 도구 중심 기능을 설명하는 데 사용됩니다. 이 서비스 정의는 Bing의 search API에서 사용 하는 서비스 계약의 작은 하위 집합입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema id="ServiceSchema"
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"
    elementFormDefault="qualified"
    xmlns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
>
  <xs:complexType name="SearchRequest">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="WebSearchOption">
    <xs:restriction base="xs:string">
      <xs:enumeration value="DisableHostCollapsing" />
      <xs:enumeration value="DisableQueryAlterations" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

 위의 서비스 계약을 프로젝트에 추가 하려면 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가 새로 만들기**...를 선택 합니다. 템플릿 대화 상자의 WCF 창에서 스키마 정의를 선택하고 새 파일의 이름을 SampleContract.xsd로 지정합니다. 위의 코드를 복사하여 새 파일의 코드 뷰에 붙여 넣습니다.

## <a name="configuring-contract-first-options"></a>도구 중심 옵션 구성

 계약 우선 옵션은 WCF 프로젝트의 속성 메뉴에서 구성할 수 있습니다. 계약 우선 개발을 사용 하려면 프로젝트 속성 창의 WCF 페이지에서 **XSD를 형식 정의 언어로 사용** 확인란을 선택 합니다.

 ![계약 우선 개발을 사용 하는 WCF 옵션의 스크린샷](./media/contract-first-tool/contract-first-options.png)

 고급 속성을 구성하려면 고급 단추를 클릭합니다.

 ![고급 계약 코드 생성 설정 대화 상자입니다.](./media/contract-first-tool/advanced-contract-settings.png)

 다음 고급 설정은 계약의 코드 생성에 대해 구성할 수 있습니다. 설정은 프로젝트의 파일 모두에 대해서만 구성할 수 있으며 이때 설정은 개별 파일에 대해 구성할 수 없습니다.

- **Serializer 모드**:이 설정은 서비스 계약 파일을 읽는 데 사용 되는 Serializer를 결정 합니다. **XML Serializer** 를 선택 하는 경우 **컬렉션 형식** 및 **재사용 유형** 옵션을 사용할 수 없습니다. 이러한 옵션은 **데이터 계약 직렬 변환기** 에만 적용 됩니다.

- **형식 다시** 사용:이 설정은 형식 재사용에 사용 되는 라이브러리를 지정 합니다. 이 설정은 **Serializer 모드** 가 **데이터 계약 Serializer** 로 설정 된 경우에만 적용 됩니다.

- **컬렉션 형식**:이 설정은 컬렉션 데이터 형식에 사용할 정규화 된 형식 또는 정규화 된 어셈블리 형식을 지정 합니다. 이 설정은 **Serializer 모드** 가 **데이터 계약 Serializer** 로 설정 된 경우에만 적용 됩니다.

- **사전 형식**:이 설정은 사전 데이터 형식에 사용할 정규화 된 형식 또는 정규화 된 어셈블리 형식을 지정 합니다.

- **Enabledatabinding**:이 설정은 <xref:System.ComponentModel.INotifyPropertyChanged> 모든 데이터 형식에 대해 인터페이스를 구현 하 여 데이터 바인딩을 구현할지 여부를 지정 합니다.

- **ExcludedTypes**:이 설정은 참조 된 어셈블리에서 제외할 정규화 된 형식 또는 정규화 된 어셈블리 형식 목록을 지정 합니다. 이 설정은 **Serializer 모드** 가 **데이터 계약 Serializer** 로 설정 된 경우에만 적용 됩니다.

- **Generateinternaltypes**:이 설정은 내부로 표시 된 클래스를 생성할지 여부를 지정 합니다. 이 설정은 **Serializer 모드** 가 **데이터 계약 Serializer** 로 설정 된 경우에만 적용 됩니다.

- **GenerateSerializableTypes**:이 설정은 특성을 사용 하 여 클래스를 생성할지 여부를 지정 합니다 <xref:System.SerializableAttribute> . 이 설정은 **Serializer 모드** 가 **데이터 계약 Serializer** 로 설정 된 경우에만 적용 됩니다.

- **Importxmltypes**:이 설정은 특성을 사용 <xref:System.SerializableAttribute> 하지 않고 클래스에 특성을 적용 하도록 데이터 계약 serializer를 구성할 지 여부를 지정 합니다 <xref:System.Runtime.Serialization.DataContractAttribute> .  이 설정은 **Serializer 모드** 가 **데이터 계약 Serializer** 로 설정 된 경우에만 적용 됩니다.

- **SupportFx35TypedDataSets**:이 설정은 .NET Framework 3.5에 대해 생성 된 형식화 된 데이터 집합에 대 한 추가 기능을 제공할지 여부를 지정 합니다. **Serializer 모드가** **xml serializer** 로 설정 된 경우 <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> 이 값이 True로 설정 되 면 확장은 xml 스키마 가져오기에서 추가 됩니다. **Serializer 모드** 가 **데이터 계약 serializer** 로 설정 된 경우 <xref:System.DateTimeOffset> 이 값이 False로 설정 되 면 해당 형식이 참조에서 제외 되므로가 <xref:System.DateTimeOffset> 항상 이전 프레임 워크 버전에 대해 생성 됩니다.

- **Inputxsdfiles**:이 설정은 입력 파일 목록을 지정 합니다. 각 파일에는 올바른 XML 스키마가 포함되어야 합니다.

- **Language**:이 설정은 생성 된 계약 코드의 언어를 지정 합니다. 이 설정은 <xref:System.CodeDom.Compiler.CodeDomProvider>에서 인식할 수 있어야 합니다.

- **NamespaceMappings**:이 설정은 XSD 대상 네임 스페이스와 CLR 네임 스페이스 간의 매핑을 지정 합니다. 각 매핑은 다음 형식을 사용해야 합니다.

    ```xml
    "Schema Namespace, CLR Namespace"
    ```

     XML Serializer는 다음 형식에서 매핑 하나만 허용됩니다.

    ```xml
    "*, CLR Namespace"
    ```

- **OutputDirectory**:이 설정은 코드 파일이 생성 될 디렉터리를 지정 합니다.

 이 설정은 프로젝트가 빌드될 때 서비스 계약 파일에서 서비스 계약 형식을 생성하는 데 사용됩니다.

## <a name="using-contract-first-development"></a>계약 중심 개발 사용

 서비스 계약을 프로젝트에 추가 하 고 빌드 설정을 확인 한 후 **F6** 키를 눌러 프로젝트를 빌드합니다. 서비스 계약에 정의된 형식은 프로젝트에서 사용할 수 있게 됩니다.

 서비스 계약에 정의된 형식을 사용하려면 현재 네임스페이스에서 `ContractTypes`에 대한 참조를 추가합니다.

```csharp
using MyProjectNamespace.ContractTypes;
```

 서비스 계약에 정의 된 형식은 다음과 같이 프로젝트에서 확인할 수 있습니다.

 ![처음 몇 문자를 입력 한 후 IntelliSense에서 표시 되는 SearchRequest 클래스입니다.](./media/contract-first-tool/service-contract-types.png)

 도구에서 생성한 형식은 GeneratedXSDTypes.cs 파일에 만들어집니다. 파일은 \<project directory> 기본적으로/sm/ \<build configuration> /Xsdgeneratedcode/directory에서 만들어집니다. 이 문서의 시작 부분에 있는 샘플 스키마는 다음과 같이 변환 됩니다.

```csharp
//------------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by a tool.
//     Runtime Version:4.0.30319.17330
//
//     Changes to this file may cause incorrect behavior and will be lost if
//     the code is regenerated.
// </auto-generated>
//------------------------------------------------------------------------------

namespace TestXSD3.ContractTypes
{
    using System.Xml.Serialization;

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Diagnostics.DebuggerStepThroughAttribute()]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]
    public partial class SearchRequest
    {

        private string versionField;

        private string marketField;

        private string uILanguageField;

        private string queryField;

        private string appIdField;

        private double latitudeField;

        private bool latitudeFieldSpecified;

        private double longitudeField;

        private bool longitudeFieldSpecified;

        private double radiusField;

        private bool radiusFieldSpecified;

        public SearchRequest()
        {
            this.versionField = "2.2";
        }

        /// <remarks/>
        [System.ComponentModel.DefaultValueAttribute("2.2")]
        public string Version
        {
            get
            {
                return this.versionField;
            }
            set
            {
                this.versionField = value;
            }
        }

        /// <remarks/>
        public string Market
        {
            get
            {
                return this.marketField;
            }
            set
            {
                this.marketField = value;
            }
        }

        /// <remarks/>
        public string UILanguage
        {
            get
            {
                return this.uILanguageField;
            }
            set
            {
                this.uILanguageField = value;
            }
        }

        /// <remarks/>
        public string Query
        {
            get
            {
                return this.queryField;
            }
            set
            {
                this.queryField = value;
            }
        }

        /// <remarks/>
        public string AppId
        {
            get
            {
                return this.appIdField;
            }
            set
            {
                this.appIdField = value;
            }
        }

        /// <remarks/>
        public double Latitude
        {
            get
            {
                return this.latitudeField;
            }
            set
            {
                this.latitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LatitudeSpecified
        {
            get
            {
                return this.latitudeFieldSpecified;
            }
            set
            {
                this.latitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Longitude
        {
            get
            {
                return this.longitudeField;
            }
            set
            {
                this.longitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LongitudeSpecified
        {
            get
            {
                return this.longitudeFieldSpecified;
            }
            set
            {
                this.longitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Radius
        {
            get
            {
                return this.radiusField;
            }
            set
            {
                this.radiusField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool RadiusSpecified
        {
            get
            {
                return this.radiusFieldSpecified;
            }
            set
            {
                this.radiusFieldSpecified = value;
            }
        }
    }

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]
    public enum WebSearchOption
    {

        /// <remarks/>
        DisableHostCollapsing,

        /// <remarks/>
        DisableQueryAlterations,
    }
}
```

## <a name="errors-and-warnings"></a>오류 및 경고

 XSD 스키마를 구문 분석할 때 발생한 오류 및 경고는 빌드 오류 및 경고로 표시됩니다.

## <a name="interface-inheritance"></a>인터페이스 상속

 계약 우선 개발을 포함하는 인터페이스 상속을 사용하는 것은 불가능하며, 다른 작업에서 인터페이스가 행동하는 방식과 일치합니다. 기본 인터페이스를 상속하는 인터페이스를 사용하려면 별도의 엔드포인트 두 개를 사용합니다. 첫 번째 엔드포인트는 상속된 계약을 사용하고, 두 번째 엔드포인트는 기본 인터페이스를 구현합니다.
