---
title: Utilisation du fournisseur WMI pour la gestion de Configuration | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 9d9f3ab9f80c6f2c77153439cf554f0ae8598586
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53351794"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Utilisation du fournisseur WMI pour la gestion de la configuration
  Tenez compte des éléments suivants avant de programmer le fournisseur WMI pour la gestion de la configuration :  
  
## <a name="binding"></a>Binding  
 Le fournisseur WMI pour la gestion de la configuration est un modèle objet COM qui prend en charge les liaisons anticipées et tardives. Avec la liaison tardive, vous pouvez utiliser des langages de script, tels que VBScript, pour manipuler par programme les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les paramètres réseau et les alias.  
  
 Pour plus d’informations sur la programmation des implémentations du fournisseur WMI à l’aide de langages de script, consultez le [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [site Web](https://go.microsoft.com/fwlink/?linkid=15426).  
  
## <a name="specifying-a-connection-string"></a>Spécification d'une chaîne de connexion  
 Les applications dirigent le fournisseur WMI pour la gestion de la configuration vers une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en se connectant à un espace de noms WMI défini par le fournisseur. Le service WMI de Windows mappe cet espace de noms à la DLL de fournisseur et la charge en mémoire. Toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont représentées avec un espace de noms WMI unique. Par défaut, l'espace de noms est  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 où `instance_name` a la valeur par défaut `MSSQLSERVER` dans une installation par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Remarque :** Si vous vous connectez via le pare-feu de Windows, vous devrez vous assurer que vos ordinateurs sont correctement configurés. Consultez l’article « Connecting Through Windows Firewall » dans la documentation Windows Management Instrumentation sur [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [site Web](https://go.microsoft.com/fwlink/?linkid=15426).  
  
## <a name="permissions-and-server-authentication"></a>Autorisations et authentification serveur  
 Pour accéder au fournisseur WMI pour la gestion de la configuration, le script de gestion WMI client doit s'exécuter dans le contexte d'un administrateur sur l'ordinateur cible. Vous devez être membre du groupe Administrateurs Windows local sur l'ordinateur à gérer.  
  
 L'administrateur peut définir des stratégies de groupe pour contrôler l'accès utilisateur aux fournisseurs WMI. Pour plus d'informations sur la définition de stratégies de groupe, consultez « Stratégie de groupe et MMC » dans l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le script de gestion WMI peut être utilisé pour mettre à jour le compte sous lequel les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutent.  
  
 Les certificats de sécurité sont pris en charge par le fournisseur WMI pour la gestion de la configuration. Pour plus d’informations sur les certificats, consultez [hiérarchie de chiffrement](../security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration SQL Server](../sql-server-configuration-manager.md)  
  
  
