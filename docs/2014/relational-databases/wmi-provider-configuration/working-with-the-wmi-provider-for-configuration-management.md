---
title: Utilisation du fournisseur WMI pour la gestion de la configuration | Microsoft Docs
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
ms.openlocfilehash: b4a4c956f1bf60f6d874ee2bda3b261dd954836d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048862"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Utilisation du fournisseur WMI pour la gestion de la configuration
  Tenez compte des éléments suivants avant de programmer le fournisseur WMI pour la gestion de la configuration :  
  
## <a name="binding"></a>Liaison  
 Le fournisseur WMI pour la gestion de la configuration est un modèle objet COM qui prend en charge les liaisons anticipées et tardives. Avec la liaison tardive, vous pouvez utiliser des langages de script, tels que VBScript, pour manipuler par programme les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les paramètres réseau et les alias.  
  
 Pour plus d’informations sur la programmation des implémentations de fournisseur WMI à l’aide de langages de script, consultez le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [site Web](https://go.microsoft.com/fwlink/?linkid=15426)MSDN.  
  
## <a name="specifying-a-connection-string"></a>Spécification d'une chaîne de connexion  
 Les applications dirigent le fournisseur WMI pour la gestion de la configuration vers une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en se connectant à un espace de noms WMI défini par le fournisseur. Le service WMI de Windows mappe cet espace de noms à la DLL de fournisseur et la charge en mémoire. Toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont représentées avec un espace de noms WMI unique. Par défaut, l'espace de noms est  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 où `instance_name` a la valeur par défaut `MSSQLSERVER` dans une installation par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Remarque :** Si vous vous connectez par le biais du pare-feu Windows, vous devez vous assurer que vos ordinateurs sont correctement configurés. Consultez l’article « connexion via le pare-feu Windows » dans la documentation Windows Management Instrumentation sur le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [site Web](https://go.microsoft.com/fwlink/?linkid=15426)MSDN.  
  
## <a name="permissions-and-server-authentication"></a>Autorisations et authentification serveur  
 Pour accéder au fournisseur WMI pour la gestion de la configuration, le script de gestion WMI client doit s'exécuter dans le contexte d'un administrateur sur l'ordinateur cible. Vous devez être membre du groupe Administrateurs Windows local sur l'ordinateur à gérer.  
  
 L'administrateur peut définir des stratégies de groupe pour contrôler l'accès utilisateur aux fournisseurs WMI. Pour plus d'informations sur la définition de stratégies de groupe, consultez « Stratégie de groupe et MMC » dans l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le script de gestion WMI peut être utilisé pour mettre à jour le compte sous lequel les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutent.  
  
 Les certificats de sécurité sont pris en charge par le fournisseur WMI pour la gestion de la configuration. Pour plus d’informations sur les certificats, consultez [hiérarchie de chiffrement](../security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration SQL Server](../sql-server-configuration-manager.md)  
  
  
