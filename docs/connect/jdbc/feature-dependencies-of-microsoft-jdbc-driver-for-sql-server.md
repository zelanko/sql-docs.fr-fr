---
title: Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 04/16/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8316978e0122fe800dbd5af592b2ed57506873b6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781950"
---
# <a name="feature-dependencies-of-the-microsoft-jdbc-driver-for-sql-server"></a>Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet article répertorie les versions dont dépend le pilote JDBC Microsoft pour SQL Server. Le projet comporte les dépendances suivantes.

## <a name="compile-time"></a>Durée de compilation

 - `com.microsoft.azure:azure-keyvault` : fournisseur Azure Key Vault pour la fonctionnalité Azure Key Vault Always Encrypted (facultatif)
 - `com.microsoft.azure:azure-keyvault-webkey` : fournisseur Azure Key Vault pour la fonctionnalité Azure Key Vault Always Encrypted (facultatif)
 - `com.microsoft.azure:adal4j` : bibliothèque Azure Active Directory pour Java pour les fonctionnalités d’authentification Azure Active Directory et Azure Key Vault (facultatif)
 - `com.microsoft.rest:client-runtime` : bibliothèque Azure Active Directory pour Java pour les fonctionnalités d’authentification Azure Active Directory et Azure Key Vault (facultatif)
- `org.osgi:org.osgi.core` : bibliothèque OSGi Core pour la prise en charge d’OSGi Framework.
- `org.osgi:org.osgi.compendium` : bibliothèque OSGi Compendium pour la prise en charge d’OSGi Framework.

## <a name="test-time"></a>Durée du test

Les projets spécifiques qui nécessitent une de ces fonctionnalités doivent déclarer explicitement les dépendances respectifs dans leur fichier POM.

**Par exemple :** lorsque vous utilisez la fonctionnalité d’authentification Azure Active Directory, vous devez redéclarer la dépendance `adal4j` dans le fichier POM du projet. Consultez l’extrait de code suivant :

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.2.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.3</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.6.5</version>
</dependency>
```

**Par exemple :** lorsque vous utilisez la fonctionnalité Azure Key Vault, vous devez redéclarer la dépendance `azure-keyvault` et la dépendance `adal4j` dans le fichier POM du projet. Consultez l’extrait de code suivant :

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.2.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.3</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.6.5</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.2.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault-webkey</artifactId>
    <version>1.2.0</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>Exigences relatives à la dépendance pour le pilote JDBC

### <a name="working-with-the-azure-key-vault-provider"></a>Utilisation du fournisseur Azure Key Vault :

- Version 7.2.2 du pilote JDBC - versions des dépendances : Azure-Keyvault (version 1.2.0), Azure-Keyvault-Webkey (version 1.2.0), Adal4j (version 1.6.3), Client-Runtime-pour-AutoRest (1.6.5). et leurs dépendances ([exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-7.0.md))
- Version 7.0.0 du pilote JDBC - versions des dépendances : Azure-Keyvault (version 1.0.0), Adal4j (version 1.6.0) et leurs dépendances ([exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-7.0.md))
- Version 6.4.0 du pilote JDBC - versions des dépendances : Azure-Keyvault (version 1.0.0), Adal4j (version 1.4.0) et leurs dépendances ([exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Version 6.2.2 du pilote JDBC - versions des dépendances : Azure-Keyvault (version 1.0.0), Adal4j (version 1.4.0) et leurs dépendances ([exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Version 6.0.0 du pilote JDBC - versions des dépendances : Azure-Keyvault (version 0.9.7), Adal4j (version 1.3.0) et leurs dépendances ([exemple d’application](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> Avec les versions de pilote 6.2.2 et 6.4.0, la dépendance azure-keyvault-java avait été mise à jour vers la version 1.0.0. Toutefois, la nouvelle version n’était pas compatible avec la version précédente (0.9.7) et arrête l’implémentation existante dans le pilote. La nouvelle implémentation dans le pilote a requis des modifications de l’API qui, à son tour, arrête les programmes clients qui utilisent le fournisseur Azure Key Vault.
>
> Ce problème est résolu avec la dernière version du pilote (7.0.0). Le constructeur supprimé qui a utilisé le mécanisme de rappel d’authentification est à nouveau ajouté au fournisseur Azure Key Vault Provider pour garantir la compatibilité descendante.

### <a name="working-with-azure-active-directory-authentication"></a>Utilisation de l’authentification Azure Active Directory :

- Version 7.2.2 du pilote JDBC - versions des dépendances : Adal4j (version 1.6.3), Client-Runtime-pour-AutoRest (1.6.5) et leurs dépendances
- Version 7.0.0 du pilote JDBC - versions des dépendances : Adal4j (version 1.6.0) et ses dépendances
- Version 6.4.0 du pilote JDBC - versions des dépendances : Adal4j (version 1.4.0) et ses dépendances
- Version 6.2.2 du pilote JDBC - versions des dépendances : Adal4j (version 1.4.0) et ses dépendances
- Version 6.0.0 du pilote JDBC - versions des dépendances : Adal4j (version 1.3.0) et ses dépendances. Dans cette version du pilote, vous ne pouvez vous connecter à l’aide du mode d’authentification _ActiveDirectoryIntegrated_ que sur un système d’exploitation Windows et à l’aide de sqljdbc_auth.dll et d’Active Directory Authentication Library pour SQL Server (ADALSQL.DLL).

À partir de la version 6.4.0 du pilote, les applications ne requièrent pas nécessairement l’utilisation d’ADALSQL.DLL sur les systèmes d’exploitation Windows. Pour les *systèmes d’exploitation autres que Windows*, le pilote a besoin d’un ticket Kerberos pour utiliser l’authentification ActiveDirectoryIntegrated. Pour plus d’informations sur la façon de se connecter à Active Directory à l’aide de Kerberos, consultez [Définir un ticket Kerberos sur Windows, Linux et Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Pour les *systèmes d’exploitation Windows*, le pilote recherche le fichier sqljdbc_auth.dll par défaut et ne requiert pas l’installation d’un ticket Kerberos ou de dépendances de la bibliothèque Azure. Si sqljdbc_auth.dll n’est pas disponible, le pilote recherche le ticket Kerberos pour l’authentification auprès d’Active Directory comme sur d’autres systèmes d’exploitation.

Vous pouvez obtenir un [exemple d’application](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md) qui utilise cette fonctionnalité.

## <a name="see-also"></a>Voir aussi

[Référentiel GitHub du pilote JDBC](https://github.com/microsoft/mssql-jdbc)  
[Informations de référence sur l’API du pilote JDBC](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
