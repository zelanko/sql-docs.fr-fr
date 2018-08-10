---
title: Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
caps.latest.revision: 57
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70179d55c6aae5fc01c84f0c4af860f86d528a06
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454223"
---
# <a name="feature-dependencies-of-microsoft-jdbc-driver-for-sql-server"></a>Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cette page répertorie les bibliothèques dont dépend de Microsoft JDBC Driver for SQL Server. Le projet comporte les dépendances suivantes.

## <a name="compile-time"></a>Durée de compilation

- `azure-keyvault`: Azure Key Vault Provider pour la fonctionnalité toujours chiffré Azure Key Vault (facultative)
- `adal4j`: La bibliothèque ActiveDirectory azure pour Java pour les fonctionnalités d’authentification Azure Active Directory et Azure Key Vault (facultatif)

## <a name="test-time"></a>Durée du test

Les projets spécifiques qui nécessitent une des deux fonctionnalités ci-dessus doivent déclarer explicitement les dépendances respectifs dans leur fichier pom :

**_Par exemple :_**  lors de l’utilisation _fonctionnalité d’authentification Azure Active Directory_, vous devez redéclarer _adal4j_ dépendance dans le fichier pom du projet. Consultez l’extrait de code suivant :

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

**_Par exemple :_**  lors de l’utilisation _la fonctionnalité Azure Key Vault_, vous devez redéclarer _azure-keyvault_ dépendance et _adal4j_ dépendance dans le fichier pom du projet. Consultez l’extrait de code suivant :

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

### <a name="working-with-azure-key-vault-provider"></a>Utilisation avec Azure Key Vault Provider :

- Le pilote JDBC version 7.0.0 - versions de dépendances : Azure-Keyvault (version 1.0.0), Adal4j (version 1.6.0) et leurs dépendances ([exemple d’Application](../../connect/jdbc/azure-key-vault-sample-version-7-0-0.md))
- Version du pilote JDBC 6.4.0 - versions de dépendances : Azure-Keyvault (version 1.0.0), Adal4j (version 1.4.0) et leurs dépendances ([exemple d’Application](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Version du pilote JDBC 6.2.2 - versions de dépendances : Azure-Keyvault (version 1.0.0), Adal4j (version 1.4.0) et leurs dépendances ([exemple d’Application](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Le pilote JDBC version 6.0.0 - versions de dépendances : Azure-Keyvault (version 0.9.7), Adal4j (version 1.3.0) et leurs dépendances ( [exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> Avec les versions de pilote v6.2.2 et v6.4.0, la dépendance d’azure-keyvault-java avait été mis à jour vers la version 1.0.0. Toutefois, la nouvelle version n’était pas compatible avec la version précédente (version 0.9.7) et par conséquent s’arrête l’implémentation existante dans le pilote. La nouvelle implémentation dans le pilote requis des modifications de l’API, qui découpe à son tour les programmes clients qui utilisent le fournisseur de coffre de clés Azure.

> Ce problème a été résolu avec v7.0.0 de version de pilote plus récente que le constructeur supprimé à l’aide du mécanisme de rappel d’authentification est ajouté au fournisseur Azure Key Vault pour descendante compatibilité.

### <a name="working-with-azure-active-directory-authentication"></a>Utilisation de l’authentification Azure Active Directory :

- Le pilote JDBC version 7.0.0 - versions de dépendances : Ada4j (version 1.6.0) et ses dépendances
- Version du pilote JDBC 6.4.0 - versions de dépendances : Adal4j (version 1.4.0) et ses dépendances
- Version du pilote JDBC 6.2.2 - versions de dépendances : Adal4j (version 1.4.0) et ses dépendances
- Le pilote JDBC version 6.0.0 - versions de dépendances : Adal4j (version 1.3.0), et ses dépendances - dans cette version du pilote, vous pouvez vous connecter à l’aide de _ActiveDirectoryIntegrated_ Mode d’authentification uniquement sur un système d’exploitation de Windows et à l’aide de sqljdbc_auth.dll et Active Directory Authentication Library pour SQL Server (ADALSQL. (DLL).

À partir de la version du pilote 6.4.0 et versions ultérieures, les applications ne requièrent pas nécessairement à l’aide de ADALSQL. DLL sur les systèmes d’exploitation Windows. Pour **les systèmes d’exploitation Non-Windows**, le pilote requiert le ticket Kerberos pour utiliser l’authentification ActiveDirectoryIntegrated. Pour plus d’informations sur comment se connecter à Active Directory à l’aide de Kerberos, consultez [ticket Kerberos défini sur Windows, Linux et Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Pour **les systèmes d’exploitation Windows**, pilote recherche sqljdbc_auth.dll par défaut et ne nécessite pas l’installation de ticket Kerberos ou des dépendances de la bibliothèque Azure. Toutefois, si sqljdbc_auth.dll n’est pas disponible, pilote recherche ticket Kerberos pour l’authentification auprès d’Active Directory en tant que sur d’autres systèmes d’exploitation.

Un exemple d’application à l’aide de cette fonctionnalité peut être trouvé [ici](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md).

## <a name="see-also"></a> Voir aussi

[Référentiel GitHub de pilote JDBC](https://github.com/microsoft/mssql-jdbc)  
 [Informations de référence sur l'API du pilote JDBC](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
