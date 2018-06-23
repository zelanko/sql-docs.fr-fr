---
title: Supprimez les références aux tables système non documentées | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd8ff349ae3e065233ea104d34016a919b9fd6e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152958"
---
# <a name="remove-references-to-undocumented-system-tables"></a>Supprimer les références aux tables système non documentées
  De nombreuses tables système qui n'étaient pas documentées dans les versions antérieures ont été modifiées ou n'existent plus. Par conséquent, l'utilisation de ces tables peut provoquer des erreurs après la mise à niveau. Étant donné que le Conseiller de mise à niveau recherche des références aux noms des tables système, il va signaler ces références à toutes les tables utilisateur qui ont le même nom que des tables système.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les tables système non documentées suivantes sont supprimées :  
  
-   **spt_datatype_info**  
  
-   **spt_datatype_info_ext**  
  
-   **spt_provider_types**  
  
-   **spt_server_info**  
  
-   **spt_values**  
  
-   **sysfulltextnotify**  
  
-   **syslocks**  
  
-   **sysproperties**  
  
-   **sysprotects_aux**  
  
-   **sysprotects_view**  
  
-   **SYSREMOTE_CATALOGS**  
  
-   **SYSREMOTE_COLUMN_PRIVILEGES**  
  
-   **SYSREMOTE_COLUMNS**  
  
-   **SYSREMOTE_FOREIGN_KEYS**  
  
-   **SYSREMOTE_INDEXES**  
  
-   **SYSREMOTE_PRIMARY_KEYS**  
  
-   **SYSREMOTE_PROVIDER_TYPES**  
  
-   **SYSREMOTE_SCHEMATA**  
  
-   **SYSREMOTE_STATISTICS**  
  
-   **SYSREMOTE_TABLE_PRIVILEGES**  
  
-   **SYSREMOTE_TABLES**  
  
-   **SYSREMOTE_VIEWS**  
  
-   **syssegments**  
  
-   **sysxlogins**  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez vos applications d'après le tableau suivant.  
  
|À la place de|Utiliser|  
|----------------|---------|  
|**sysfulltextnotify**|propriété**TableFulltextPendingChanges** de la fonction OBJECTPROPERTYEX.|  
|**syslocks**|vue de gestion dynamique**sys.dm_tran_locks** , sp_lock, ou vue de compatibilité **sys.syslockinfo** .|  
|**sysproperties**|affichage catalogue**sys.extended_properties** ou fonction **fn_listextendedproperty** |  
|**sysxlogins**|affichage catalogue**sys.server_principals** ou vue de compatibilité **syslogins** |  
|toutes les tables **spt_**|Aucun remplacement disponible|  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
