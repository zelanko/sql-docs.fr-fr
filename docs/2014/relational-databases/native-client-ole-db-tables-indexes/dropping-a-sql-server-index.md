---
title: Suppression d’un Index SQL Server | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 38e103cd19950846dd9c88d0b4bdc0d5d385ba1f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042907"
---
# <a name="dropping-a-sql-server-index"></a>Suppression d'un index SQL Server
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **IIndexDefinition::DropIndex** (fonction). Cela permet aux consommateurs de supprimer un index à partir d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose certains [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des contraintes PRIMARY KEY et UNIQUE en tant qu’index. Propriétaire de la table, le propriétaire de la base de données et certains membres du rôle d’administrateur peuvent modifier un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, la suppression d’une contrainte. Par défaut, seul le propriétaire de la table peut supprimer un index existant. Par conséquent, **DropIndex** réussite ou l’échec dépend non seulement de droits d’accès de l’utilisateur de l’application, mais également sur le type d’index indiqué.  
  
 Les consommateurs spécifient le nom de la table en tant que chaîne de caractères Unicode dans le *pwszName* membre de la *uName* union dans la *pTableID* paramètre. Le *eKind* membre *pTableID* doit être DBKIND_NAME.  
  
 Les consommateurs spécifient le nom de l’index en tant que chaîne de caractères Unicode dans le *pwszName* membre de la *uName* union dans la *pIndexID* paramètre. Le *eKind* membre *pIndexID* doit être DBKIND_NAME. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne prend pas en charge la fonctionnalité OLE DB de la suppression de tous les index sur une table lorsque *pIndexID* a la valeur null. Si *pIndexID* est null, E_INVALIDARG est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et des index](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
