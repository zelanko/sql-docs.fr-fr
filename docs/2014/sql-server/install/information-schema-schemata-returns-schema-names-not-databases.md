---
title: INFORMATION_SCHEMA. Noms de schéma retourne de schémas dans une base de données, pas les bases de données dans une instance | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e624597090ab6a7efdb21ebbff6785b1471d7367
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153379"
---
# <a name="informationschemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA retourne les noms de schémas dans une base de données, pas les bases de données dans une instance
  Le Conseiller de mise à niveau a détecté des instructions faisant référence à la vue INFORMATION_SCHEMA.SCHEMATA. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette vue retourne toutes les bases de données d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, la vue retourne tous les schémas d'une base de données.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la vue INFORMATION_SCHEMA.SCHEMATA retourne toutes les bases de données d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La vue retourne tous les schémas d'une base de données, conformément à la norme SQL.  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez votre application pour faire référence à la **sys.databases** affichage pour retourner toutes les bases de données dans une instance de catalogue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
