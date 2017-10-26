---
title: external scripts enabled (option de configuration de serveur) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 08/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external scripts enabled
- external_scripts_enabled_TSQL
helpviewer_keywords:
- external scripts enabled option
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 74f73ab33a010583b4747fcc2d9b35d6cdea14a2
ms.openlocfilehash: 282f50334b59e2d41e2fcac7e33835859bdffe12
ms.contentlocale: fr-fr
ms.lasthandoff: 08/04/2017

---
# <a name="external-scripts-enabled-server-configuration-option"></a>external scripts enabled (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **external scripts enabled** pour activer l’exécution de scripts avec certaines extensions de langage à distance. Cette propriété est désactivée par défaut. Quand **Advanced Analytics Services** est installé, le programme d’installation peut éventuellement définir cette propriété sur True.  
  

 Vous devez activer l’option de scripts externes activés avant de pouvoir exécuter un script externe à l’aide de la procédure **sp_execute_external_script** . Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans un langage pris en charge, tels que R. Dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] comprend un composant de serveur installé avec [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], ainsi qu’un ensemble d’outils de station de travail et de bibliothèques de connectivité qui connectent les données scientifiques à l’environnement hautes performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Installez la fonction **Extensions analytiques avancées** pendant l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre l’exécution de scripts R. Pour plus d’informations, voir [Installing Previous Versions of SQL Server R Services](http://msdn.microsoft.com/library/48380645-9e72-4744-bebb-1c1fd8a18c43).  
  
 Pour activer les scripts externes, exécutez le script suivant :  
  
```  
sp_configure 'external scripts enabled', 1;  
RECONFIGURE WITH OVERRIDE;  
```  
  
 Vous devez redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour que ce changement soit effectif.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  

