---
title: Suppression d’un Index SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 148565f2866e571ba783c58d1ff10413510ef6db
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422228"
---
# <a name="dropping-a-sql-server-index"></a>Suppression d'un index SQL Server
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **IIndexDefinition::DropIndex** (fonction). Cela permet aux consommateurs de supprimer un index à partir d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose certains [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des contraintes PRIMARY KEY et UNIQUE en tant qu’index. Propriétaire de la table, le propriétaire de la base de données et certains membres du rôle d’administrateur peuvent modifier un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, la suppression d’une contrainte. Par défaut, seul le propriétaire de la table peut supprimer un index existant. Par conséquent, **DropIndex** réussite ou l’échec dépend non seulement les droits d’accès d’utilisateur de l’application, mais également sur le type d’index indiqué.  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le *pwszName* membre de la *uName* union dans le *pTableID* paramètre. Le *eKind* membre *pTableID* doit être DBKIND_NAME.  
  
 Les consommateurs spécifient le nom d’index en tant que chaîne de caractères Unicode dans le *pwszName* membre de la *uName* union dans le *pIndexID* paramètre. Le *eKind* membre *pIndexID* doit être DBKIND_NAME. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne prend pas en charge la fonctionnalité OLE DB de la suppression de tous les index sur une table lorsque *pIndexID* a la valeur null. Si *pIndexID* est null, E_INVALIDARG est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
