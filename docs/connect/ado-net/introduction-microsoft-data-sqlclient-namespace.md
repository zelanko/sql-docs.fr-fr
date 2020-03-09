---
title: Présentation de l’espace de noms Microsoft.Data.SqlClient
description: Page de présentation de l’espace de noms Microsoft.Data.SqlClient.
ms.date: 09/30/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: dbc76f1a2ee93faf642d923d3a543eee40d5348b
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78897120"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Présentation de l’espace de noms Microsoft.Data.SqlClient

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

## <a name="release-notes-for-microsoftdatasqlclient-110"></a>Notes de publication de Microsoft.Data.SqlPackage 1.1.0

Les notes de publication sont également disponibles dans le référentiel GitHub : [1.1 Notes de publication](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1).

### <a name="new-features"></a>Nouvelles fonctionnalités

#### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted avec enclaves sécurisées

Always Encrypted est disponible à partir de Microsoft SQL Server 2016. Les enclaves sécurisées sont disponibles à partir de Microsoft SQL Server 2019. Pour pouvoir utiliser la fonctionnalité d’enclave, les chaînes de connexion doivent inclure le protocole d’attestation et l’URL d’attestation requis. Exemples :

```
Attestation Protocol=HGS;Enclave Attestation Url=<attestation_url_for_HGS>
```

Pour plus d'informations, consultez la page suivante :

- [Support SqlClient pour Always Encrypted](sql/sqlclient-support-always-encrypted.md)
- [Tutoriel : Développer une application .NET en utilisant Always Encrypted avec enclaves sécurisées](sql/tutorial-always-encrypted-enclaves-develop-net-apps.md)

## <a name="release-notes-for-microsoftdatasqlclient-10"></a>Notes de publication pour Microsoft.Data.SqlPackage 1.0

La version initiale de l’espace de noms Microsoft.Data.SqlClient offre des fonctionnalités supplémentaires par rapport à l’espace de noms System.Data.SqlClient existant.
Les notes de publication sont également disponibles dans le référentiel GitHub : [Notes de publication 1.0](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.0).

### <a name="new-features"></a>Nouvelles fonctionnalités

#### <a name="new-features-over-net-framework-472-systemdatasqlclient"></a>Nouvelles fonctionnalités de .NET Framework 4.7.2 System.Data.SqlClient

- **Classification des données** : disponible dans Azure SQL Database et Microsoft SQL Server 2019.

- **Support UTF-8** : disponible dans Microsoft SQL Server 2019.

#### <a name="new-features-over-net-core-22-systemdatasqlclient"></a>Nouvelles fonctionnalités de .NET Core 2.2 System.Data.SqlClient

- **Classification des données** : disponible dans Azure SQL Database et Microsoft SQL Server 2019.

- **Support UTF-8** : disponible dans Microsoft SQL Server 2019.

- **Authentification** : mode d’authentification du mot de passe Active Directory.

### <a name="data-classification"></a>Classification des données

La classification des données apporte un nouvel ensemble d’API exposant la sensibilité des données en lecture seule et des informations de classification sur les objets récupérés par le biais de SqlDataReader lorsque la source sous-jacente prend en charge la fonctionnalité et contient des métadonnées sur la [sensibilité et la classification des données](../../relational-databases/security/sql-data-discovery-and-classification.md).

```csharp
public class SqlDataReader
{
    public Microsoft.Data.SqlClient.DataClassification.SensitivityClassification SensitivityClassification
}

namespace Microsoft.Data.SqlClient.DataClassification
{
    public class ColumnSensitivity
    {
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.SensitivityProperty> SensitivityProperties
    }
    public class InformationType
    {
        public string Id
        public string Name
    }
    public class Label
    {
        public string Id
        public string Name
    }
    public class SensitivityClassification
    {
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.ColumnSensitivity> ColumnSensitivities
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.InformationType> InformationTypes
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.Label> Labels
    }
    public class SensitivityProperty
    {
        public Microsoft.Data.SqlClient.DataClassification.InformationType InformationType
        public Microsoft.Data.SqlClient.DataClassification.Label Label
    }
}
```

### <a name="utf-8-support"></a>Prise en charge d’UTF-8

Le support UTF-8 ne requiert aucune modification du code de l’application. Ces modifications SqlClient optimisent simplement la communication entre le client et le serveur lorsque le serveur prend en charge UTF-8 et que le classement de la colonne sous-jacente est UTF-8. Consultez la section UTF-8 sous [Nouveautés de SQL Server préversion de 2019](../../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="always-encrypted-with-enclaves"></a>Always Encrypted avec enclaves

En général, la documentation existante qui utilise System.Data.SqlClient sur .NET Framework **et les fournisseurs de magasin de clés principales de colonne intégrés** doit désormais fonctionner également avec .NET Core.

 [Développer à l’aide d’Always Encrypted avec le fournisseur de données .NET Framework](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted : Protéger les données sensibles et stocker les clés de chiffrement dans le magasin de certificats Windows](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>Authentication

Vous pouvez spécifier différents modes d’authentification à l’aide de l’option de chaîne de connexion _Authentification_. Pour plus d’informations, consultez la [documentation de SqlAuthenticationMethod](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2).

> [!NOTE]
> Les fournisseurs de magasins de clés personnalisés, comme le fournisseur d’Azure Key Vault, devront être mis à jour pour prendre en charge Microsoft.Data.SqlClient. De même, les fournisseurs d’enclaves devront également être mis à jour pour prendre en charge Microsoft.Data.SqlClient.
> Always Encrypted est pris en charge uniquement sur les cibles .NET Framework et .NET Core. Il n’est pas pris en charge sur .NET Standard dans la mesure où certaines dépendances de chiffrement manquent dans .NET Standard.
