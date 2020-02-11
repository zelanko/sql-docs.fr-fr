---
title: Utiliser le fournisseur WMI pour la gestion de la configuration
ms.custom: seo-lt-2019
ms.date: 04/12/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d76cc006e2f8638de9b6d3c21660806239022ec0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73657376"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Utilisation du fournisseur WMI pour la gestion de la configuration

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Cet article fournit des conseils sur la façon de programmer avec le fournisseur WMI pour la gestion de l’ordinateur.

## <a name="binding"></a>Liaison  
 Le fournisseur WMI pour la gestion de la configuration est un modèle objet COM qui prend en charge les liaisons anticipées et tardives. Avec la liaison tardive, vous pouvez utiliser des langages de script, tels que VBScript, pour manipuler par programme les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les paramètres réseau et les alias.  
  
## <a name="specifying-a-connection-string"></a>Spécification d'une chaîne de connexion

Les applications dirigent le fournisseur WMI pour la gestion de la configuration vers une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en se connectant à un espace de noms WMI défini par le fournisseur. Le service WMI de Windows mappe cet espace de noms à la DLL du fournisseur et charge la DLL en mémoire. Toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont représentées avec un espace de noms WMI unique.

L’espace de noms est par défaut au format suivant. Dans le format, `VV` est le numéro de version principale de SQL Server. Le nombre peut être découvert en exécutant `SELECT @@VERSION;`.

```console
\\.\root\Microsoft\SqlServer\ComputerManagementVV
```

Lorsque vous vous connectez à l’aide de PowerShell `\\.\` , le début doit être supprimé. Par exemple, le code PowerShell suivant répertorie toutes les classes WMI pour une SQL Server 2016, qui est la version majeure de la version 13.

```powershell
Get-WmiObject -Namespace 'root\Microsoft\SqlServer\ComputerManagement13' -List
```

<!--
Updated this on 2019-04-12, per:
   ~ https://github.com/MicrosoftDocs/sql-docs/issues/1817
   ~ https://github.com/rrg92/sql-docs/commit/3d518bfc0d55f819c762abc3e5c5c9eed85abe94?diff=unified

Thus from here I (GeneMi = MightyPen) removed the following text about 'instance_name':

'root\Microsoft\SqlServer\ComputerManagement13\instance_name'

where `instance_name` defaults to `MSSQLSERVER` in a default installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
-->

Vous pouvez utiliser le code PowerShell suivant pour interroger tous les espaces de noms WMI ComputerManagement disponibles.

```powershell
gwmi -ns 'root\Microsoft\SqlServer' __NAMESPACE | ? {$_.name -match 'ComputerManagement' } | select name
```

 **Remarque :** Si vous vous connectez par le biais du pare-feu Windows, vous devez vous assurer que vos ordinateurs sont correctement configurés. Consultez l’article « connexion via le pare-feu Windows » dans la [!INCLUDE[msCoName](../../includes/msconame-md.md)] documentation Windows Management Instrumentation sur le [site Web](https://go.microsoft.com/fwlink/?linkid=15426)MSDN.  
  
## <a name="permissions-and-server-authentication"></a>Autorisations et authentification serveur  
 Pour accéder au fournisseur WMI pour la gestion de la configuration, le script de gestion WMI client doit s'exécuter dans le contexte d'un administrateur sur l'ordinateur cible. Vous devez être membre du groupe Administrateurs Windows local sur l'ordinateur à gérer.  
  
 L'administrateur peut définir des stratégies de groupe pour contrôler l'accès utilisateur aux fournisseurs WMI. Pour plus d'informations sur la définition de stratégies de groupe, consultez « Stratégie de groupe et MMC » dans l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le script de gestion WMI peut être utilisé pour mettre à jour le compte sous lequel les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutent.  
  
 Les certificats de sécurité sont pris en charge par le fournisseur WMI pour la gestion de la configuration. Pour plus d’informations sur les certificats, consultez [hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  
