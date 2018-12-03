---
title: Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01388e48e12a01e18b837cac8e663bf2f52ebe40
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52502628"
---
# <a name="feature-dependencies-of-the-microsoft-jdbc-driver-for-sql-server"></a>Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server.

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet article répertorie les bibliothèques qui dépend de Microsoft JDBC Driver for SQL Server. Le projet comporte les dépendances suivantes.

## <a name="compile-time"></a>Durée de compilation

- `azure-keyvault`: Azure Key Vault Provider pour la fonctionnalité toujours chiffré Azure Key Vault (facultative)
- `adal4j`: Bibliothèque azure Active Directory pour Java pour la fonctionnalité d’authentification Azure Active Directory et la fonctionnalité Azure Key Vault (facultative)

## <a name="test-time"></a>Durée du test

Les projets spécifiques qui nécessitent une de ces fonctionnalités doivent déclarer explicitement les dépendances respectifs dans leur fichier POM.

**Par exemple :** lorsque vous utilisez la fonctionnalité d’authentification Azure Active Directory, vous devez redéclarer la `adal4j` dépendance dans le fichier POM du projet. Consultez l’extrait de code suivant :

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>
```

**Par exemple :** lorsque vous utilisez la fonctionnalité Azure Key Vault, vous devez redéclarer la `azure-keyvault` dépendance et le `adal4j` dépendance dans le fichier POM du projet. Consultez l’extrait de code suivant :

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.0.0</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>Configuration requise de dépendance pour le pilote JDBC

### <a name="working-with-the-azure-key-vault-provider"></a>Utilisation du fournisseur Azure Key Vault :

- Le pilote JDBC version 7.0.0 - versions de dépendances : Azure-Keyvault (version 1.0.0), Adal4j (version 1.6.0) et leurs dépendances ([exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-7-0-0.md))
- Version du pilote JDBC 6.4.0 - versions de dépendances : Azure-Keyvault (version 1.0.0), Adal4j (version 1.4.0) et leurs dépendances ([exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Version du pilote JDBC 6.2.2 - versions de dépendances : Azure-Keyvault (version 1.0.0), Adal4j (version 1.4.0) et leurs dépendances ([exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Le pilote JDBC version 6.0.0 - versions de dépendances : Azure-Keyvault (version 0.9.7), Adal4j (version 1.3.0) et leurs dépendances ( [exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> Avec les versions de pilote 6.2.2 et 6.4.0, la dépendance d’azure-keyvault-java avait été mis à jour vers la version 1.0.0. Toutefois, la nouvelle version n’était pas compatible avec la version précédente (0.9.7) et s’arrête l’implémentation existante dans le pilote. La nouvelle implémentation dans le pilote requis des modifications de l’API, qui découpe à son tour les programmes clients qui utilisent le fournisseur de coffre de clés Azure.
>
> Ce problème est résolu avec la dernière version de pilote (7.0.0). Le constructeur supprimé qui a utilisé le mécanisme de rappel d’authentification est ajouté à l’Azure Key Vault Provider pour la compatibilité descendante.

### <a name="working-with-azure-active-directory-authentication"></a>Utilisation de l’authentification Azure Active Directory :

- Le pilote JDBC version 7.0.0 - versions de dépendances : Ada4j (version 1.6.0) et ses dépendances
- Version du pilote JDBC 6.4.0 - versions de dépendances : Adal4j (version 1.4.0) et ses dépendances
- Version du pilote JDBC 6.2.2 - versions de dépendances : Adal4j (version 1.4.0) et ses dépendances
- Le pilote JDBC version 6.0.0 - versions de dépendances : Adal4j (version 1.3.0) et ses dépendances. Dans cette version du pilote, vous pouvez vous connecter à l’aide de _ActiveDirectoryIntegrated_ Mode d’authentification uniquement sur un système d’exploitation de Windows et à l’aide de sqljdbc_auth.dll et Active Directory Authentication Library pour SQL Server () ADALSQL. (DLL).

À partir de la version du pilote 6.4.0 dès lors, les applications ne requièrent pas nécessairement à l’aide de ADALSQL. DLL sur les systèmes d’exploitation Windows. Pour *les systèmes d’exploitation non Windows*, le pilote nécessite un ticket Kerberos pour utiliser l’authentification ActiveDirectoryIntegrated. Pour plus d’informations sur comment se connecter à Active Directory à l’aide de Kerberos, consultez [ticket Kerberos défini sur Windows, Linux et Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Pour *les systèmes d’exploitation Windows*, le pilote recherche sqljdbc_auth.dll par défaut et ne nécessite pas l’installation de ticket Kerberos ou des dépendances de la bibliothèque Azure. Si sqljdbc_auth.dll n’est pas disponible, le pilote recherche le ticket Kerberos pour l’authentification auprès d’Active Directory en tant que sur d’autres systèmes d’exploitation.

Vous pouvez obtenir un [exemple d’application](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md) qui utilise cette fonctionnalité.

## <a name="see-also"></a>Voir aussi

[Référentiel GitHub du pilote JDBC](https://github.com/microsoft/mssql-jdbc)  
 [Informations de référence sur l’API du pilote JDBC](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
