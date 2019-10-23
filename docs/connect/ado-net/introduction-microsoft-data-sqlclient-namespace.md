---
title: Présentation de l’espace de noms Microsoft.Data.SqlClient
description: Page d’introduction de l’espace de noms Microsoft. Data. SqlClient.
ms.date: 09/30/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 4f4034c557c13054dcfb6ed425ca996b0c5363f6
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452381"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Présentation de l’espace de noms Microsoft.Data.SqlClient

![Download-DownArrow-Circled](../../ssdt/media/download.png)[Télécharger ADO.NET](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Cette page décrit comment l’espace de noms Microsoft. Data. SqlClient offre des fonctionnalités supplémentaires par rapport à l’espace de noms System. Data. SqlClient existant.
  
## <a name="release-notes"></a>Notes de publication
Toutes les notes de publication sont disponibles dans le [référentiel GitHub](https://github.com/dotnet/SqlClient/tree/master/release-notes).

## <a name="new-features"></a>Nouvelles fonctionnalités

### <a name="new-features-over-net-framework-472-systemdatasqlclient"></a>Nouvelles fonctionnalités de .NET Framework 4.7.2 System. Data. SqlClient

Classification des données : disponible dans Azure SQL Database et Microsoft SQL Server 2019 depuis CTP 2,0.

Prise en charge d’UTF-8 : disponible en Microsoft SQL Server SQL Server 2019 depuis CTP 2,3.

### <a name="new-features-over-net-core-22-systemdatasqlclient"></a>Nouvelles fonctionnalités de .NET Core 2,2 System. Data. SqlClient

Classification des données : disponible dans Azure SQL Database et Microsoft SQL Server 2019 depuis CTP 2,0.

Prise en charge d’UTF-8 : disponible en Microsoft SQL Server SQL Server 2019 depuis CTP 2,3.

Always Encrypted avec enclaves-Always Encrypted est disponible dans Microsoft SQL Server 2016 et versions ultérieures. La prise en charge de l’enclave a été introduite dans Microsoft SQL Server 2019 CTP 2,0.

Authentification : mode d’authentification par mot de passe Active Directory.

### <a name="data-classification"></a>Classification des données

La classification des données apporte un nouvel ensemble d’API exposant la sensibilité des données en lecture seule et des informations de classification sur les objets récupérés par le SqlDataReader lorsque la source sous-jacente prend en charge la fonctionnalité et contient des métadonnées sur la [sensibilité des données et classification](../../relational-databases/security/sql-data-discovery-and-classification.md).

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

La prise en charge d’UTF-8 ne requiert aucune modification du code de l’application. Ces modifications SqlClient optimisent simplement la communication entre le client et le serveur lorsque le serveur prend en charge UTF-8 et que le classement de la colonne sous-jacente est UTF-8. Consultez la section UTF-8 sous [what’s New in SQL Server 2019 Preview](../../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="always-encrypted-with-enclaves"></a>Always Encrypted avec enclaves

En général, la documentation existante qui utilise System. Data. SqlClient sur .NET Framework **et les fournisseurs de magasins de clés principales de colonne intégrés** doit maintenant fonctionner avec .net core.

 [Développer à l’aide d’Always Encrypted avec le fournisseur de données .NET Framework](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted : protéger des données sensibles et stocker des clés de chiffrement dans le magasin de certificats Windows](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>Authentification

Vous pouvez spécifier différents modes d’authentification à l’aide de l’option de chaîne de connexion _Authentication_ . Pour plus d’informations, consultez la [documentation de SqlAuthenticationMethod](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2).

> [!NOTE]
> Les fournisseurs de magasins de clés personnalisés, comme le fournisseur de Azure Key Vault, devront être mis à jour pour prendre en charge Microsoft. Data. SqlClient. De même, les fournisseurs d’enclave devront également être mis à jour pour prendre en charge Microsoft. Data. SqlClient.
> Always Encrypted est pris en charge uniquement sur les cibles .NET Framework et .NET Core. Il n’est pas pris en charge par rapport à .NET Standard dans la mesure où certaines dépendances de chiffrement manquent .NET Standard.
