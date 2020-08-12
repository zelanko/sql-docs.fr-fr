---
title: Présentation de l’espace de noms Microsoft.Data.SqlClient
description: Page de présentation de l’espace de noms Microsoft.Data.SqlClient.
ms.date: 06/23/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 3a4f0611d3708aba9557deb81ab702f29e7a7462
ms.sourcegitcommit: 22f687e9e8b4f37b877b2d19c5090dade8fa26d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334586"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Présentation de l’espace de noms Microsoft.Data.SqlClient

[!INCLUDE [Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

## <a name="release-notes-for-microsoftdatasqlclient-20"></a>Notes de publication de Microsoft.Data.SqlClient 2.0

Les notes de publication sont également disponibles dans le référentiel GitHub : [Notes de publication 2.0](https://github.com/dotnet/SqlClient/tree/master/release-notes/2.0).

### <a name="breaking-changes"></a>Changements cassants

- Le modificateur d’accès de l’interface du fournisseur d’enclave `SqlColumnEncryptionEnclaveProvider` (`public`) a été remplacé par `internal`.

- Les constantes de la classe `SqlClientMetaDataCollectionNames` ont été mises à jour pour refléter les modifications apportées à SQL Server.

- Le pilote effectue maintenant une validation du certificat de serveur lorsque le serveur SQL Server cible applique le chiffrement TLS, soit le comportement par défaut pour les connexions Azure.

- `SqlDataReader.GetSchemaTable()` retourne maintenant une `DataTable` vide à la place de `null`.

- Le pilote effectue maintenant un arrondi d’échelle décimale, calqué sur le comportement de SQL Server. À des fins de compatibilité descendante, le comportement de troncation précédent peut être activé à l’aide d’un commutateur AppContext.

- Pour les applications .NET Framework qui consomment **Microsoft.Data.SqlClient**, les fichiers SNI.dll, auparavant téléchargés dans les dossiers `bin\x64` et `bin\x86`, sont maintenant nommés `Microsoft.Data.SqlClient.SNI.x64.dll` et ` Microsoft.Data.SqlClient.SNI.x86.dll`, et téléchargés dans le répertoire `bin`.

- De nouveaux synonymes des propriétés de chaîne de connexion remplacent les anciennes propriétés lors de l’extraction de la chaîne de connexion auprès de `SqlConnectionStringBuilder` à des fins de cohérence. [En savoir plus](#new-connection-string-property-synonyms)

### <a name="new-features"></a>Nouvelles fonctionnalités

#### <a name="dns-failure-resiliency"></a>Résilience des échecs DNS

Le pilote met maintenant en cache les adresses IP issues de toutes les connexions réussies dans un point de terminaison SQL Server qui prend en charge la fonctionnalité. En cas d’échec de la résolution DNS lors d’une tentative de connexion, il tente d’établir une connexion à l’aide d’une adresse IP en cache, s’il en existe une pour ce serveur. 

#### <a name="eventsource-tracing"></a>Suivi EventSource

Cette version introduit la prise en charge de la capture des journaux de suivi d’événements pour les applications de débogage. Pour capturer ces événements, les applications clientes doivent les détecter dans l’implémentation EventSource de SqlClient :

```
Microsoft.Data.SqlClient.EventSource
```

Pour plus d’informations, consultez [Guide pratique pour activer le suivi d’événements dans SqlClient](enable-eventsource-tracing.md).

#### <a name="enabling-managed-networking-on-windows"></a>Activation de la mise en réseau gérée sur Windows

Un nouveau commutateur AppContext, **Switch.Microsoft.Data.SqlClient.UseManagedNetworkingOnWindows**, permet d’utiliser une implémentation SNI gérée sur Windows à des fins de test et de débogage. Il modifie le comportement du pilote de façon à utiliser une indication SNI gérée dans les projets .NET Core 2.1 (et versions ultérieures) et .NET Standard 2.0 (et versions ultérieures) sur Windows, éliminant ainsi toutes les dépendances vis-à-vis de bibliothèques natives pour la bibliothèque Microsoft.Data.SqlClient.

```csharp
AppContext.SetSwitch("Switch.Microsoft.Data.SqlClient.UseManagedNetworkingOnWindows", true);
```

Pour obtenir la liste complète des commutateurs disponibles dans le pilote, consultez [Commutateurs AppContext dans SqlClient](appcontext-switches.md).

#### <a name="enabling-decimal-truncation-behavior"></a>Activation du comportement de troncation décimale 

L’échelle de données décimale est arrondie par défaut par le pilote, comme le fait SQL Server. À des fins de compatibilité descendante, vous pouvez définir le commutateur AppContext **Switch.Microsoft.Data.SqlClient.TruncateScaledDecimal** sur **true**.

```csharp
AppContext.SetSwitch("Switch.Microsoft.Data.SqlClient.TruncateScaledDecimal", true);
```

#### <a name="new-connection-string-property-synonyms"></a>Nouveaux synonymes des propriétés de chaîne de connexion

De nouveaux synonymes ont été ajoutés pour les propriétés de chaîne de connexion existantes suivantes afin d’éviter toute confusion liée à l’espacement entre les propriétés comportant plusieurs mots. Les anciens noms des propriétés resteront pris en charge à des fins de compatibilité descendante, mais les nouvelles propriétés de chaîne de connexion seront désormais incluses lors de l’extraction de la chaîne de connexion auprès de [SqlConnectionStringBuilder](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlclient.sqlconnectionstringbuilder).

|Propriété de chaîne de connexion existante|Nouveau synonyme|
|-----------------------------------|-----------|
| ApplicationIntent | Intention de l'application |
| ConnectRetryCount | Nombre de nouvelles tentatives de connexion |
| ConnectRetryInterval | Intervalle avant nouvelle tentative de connexion |
| PoolBlockingPeriod | Période de blocage du pool |
| MultipleActiveResultSets | Jeux MARS (Multiple Active Result Set) |
| MultiSubnetFailover | Basculement de plusieurs sous-réseaux |
| TransparentNetworkIPResolution | Résolution transparente d’adresses IP réseau |
| TrustServerCertificate | Faire confiance au certificat de serveur |

#### <a name="sqlbulkcopy-rowscopied-property"></a>Propriété SqlBulkCopy RowsCopied

La propriété RowsCopied fournit un accès en lecture seule au nombre de lignes traitées dans l’opération de copie en bloc en cours. Cette valeur n’est pas nécessairement égale au nombre final de lignes ajoutées à la table de destination. 

#### <a name="connection-open-overrides"></a>Remplacement de Connection.Open

Le comportement par défaut de SqlConnection.Open() peut être écrasé pour désactiver le délai de dix secondes et les tentatives de connexion automatiques déclenchées par des erreurs temporaires.

```csharp
using SqlConnection sqlConnection = new SqlConnection("Data Source=(local);Integrated Security=true;Initial Catalog=AdventureWorks;");
sqlConnection.Open(SqlConnectionOverrides.OpenWithoutRetry);
```

> [!NOTE]
> Notez que ce remplacement ne s’applique qu’à SqlConnection.Open() et non à SqlConnection.OpenAsync().

#### <a name="username-support-for-active-directory-interactive-mode"></a>Prise en charge du nom d’utilisateur pour le mode interactif Active Directory

Un nom d’utilisateur peut être spécifié dans la chaîne de connexion avec le mode d’authentification interactive Azure Active Directory pour .NET Framework et .NET Core.

Définissez un nom d’utilisateur à l’aide de la propriété de chaîne de connexion **User ID** ou **UID** :

```
"Server=<server name>; Database=<db name>; Authentication=Active Directory Interactive; User Id=<username>;"
```

#### <a name="order-hints-for-sqlbulkcopy"></a>Indicateurs d’ordre pour SqlBulkCopy

Des indicateurs d’ordre peuvent être spécifiés pour améliorer les performances des opérations de copie en bloc sur les tables avec index cluster. Pour plus d’informations, consultez la section [Opérations de copie en bloc](sql/bulk-copy-order-hints.md).

#### <a name="sni-dependency-changes"></a>Modification des dépendances SNI

Microsoft.Data.SqlClient (.NET Core et .NET Standard) sur Windows dépend maintenant de **Microsoft.Data.SqlClient.SNI.runtime**, et non plus de **runtime.native.System.Data.SqlClient.SNI**. La nouvelle dépendance ajoute la prise en charge de la plateforme ARM à celle des plateformes déjà prises en charge (ARM64, x64 et x86) sur Windows.

## <a name="release-notes-for-microsoftdatasqlclient-110"></a>Notes de publication de Microsoft.Data.SqlPackage 1.1.0

Les notes de publication sont également disponibles dans le référentiel GitHub : [1.1 Notes de publication](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1).

### <a name="new-features"></a>Nouvelles fonctionnalités

#### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted avec enclaves sécurisées

Always Encrypted est disponible à partir de Microsoft SQL Server 2016. Les enclaves sécurisées sont disponibles à partir de Microsoft SQL Server 2019. La fonctionnalité d’enclave ne peut être utilisée que si les chaînes de connexion incluent le protocole d’attestation et l’URL d’attestation requis. Par exemple :

```
Attestation Protocol=HGS;Enclave Attestation Url=<attestation_url_for_HGS>
```

Pour plus d'informations, consultez les pages suivantes :

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

La classification des données apporte un nouvel ensemble d’API exposant la sensibilité des données en lecture seule et des informations de classification sur les objets récupérés par le biais de SqlDataReader lorsque la source sous-jacente prend en charge la fonctionnalité et contient des métadonnées sur la [sensibilité et la classification des données](../../relational-databases/security/sql-data-discovery-and-classification.md). Consultez l’exemple d’application dans [Découverte et classification des données dans SqlClient](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1).

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

Le support UTF-8 ne requiert aucune modification du code de l’application. Ces modifications SqlClient optimisent la communication client-serveur lorsque le serveur prend en charge l’encodage UTF-8 et que le classement de la colonne sous-jacente est en UTF-8. Consultez la section UTF-8 sous [Nouveautés de SQL Server préversion de 2019](../../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="always-encrypted-with-enclaves"></a>Always Encrypted avec enclaves

En général, la documentation existante qui utilise System.Data.SqlClient sur .NET Framework **et les fournisseurs de magasin de clés principales de colonne intégrés** doit désormais fonctionner également avec .NET Core.

 [Développer à l’aide d’Always Encrypted avec le fournisseur de données .NET Framework](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted : Protéger les données sensibles et stocker les clés de chiffrement dans le magasin de certificats Windows](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>Authentification

Vous pouvez spécifier différents modes d’authentification à l’aide de l’option de chaîne de connexion _Authentification_. Pour plus d’informations, consultez la [documentation de SqlAuthenticationMethod](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2).

> [!NOTE]
> Les fournisseurs de magasins de clés personnalisés, comme le fournisseur d’Azure Key Vault, devront être mis à jour pour prendre en charge Microsoft.Data.SqlClient. De même, les fournisseurs d’enclaves devront également être mis à jour pour prendre en charge Microsoft.Data.SqlClient.
> Always Encrypted est pris en charge uniquement sur les cibles .NET Framework et .NET Core. Il n’est pas pris en charge sur .NET Standard dans la mesure où certaines dépendances de chiffrement manquent dans .NET Standard.
