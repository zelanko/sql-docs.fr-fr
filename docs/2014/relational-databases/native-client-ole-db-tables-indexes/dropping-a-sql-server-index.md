---
title: Suppression d’un index de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14b54b80d18b79092ab46055477b59cb4ea6d5ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046386"
---
# <a name="dropping-a-sql-server-index"></a>Suppression d'un index SQL Server
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client expose la fonction **IIndexDefinition ::D ropindex** . Cela permet aux consommateurs de supprimer un index d’une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] certaines contraintes de clé primaire et uniques en tant qu’index. Le propriétaire de la table, le propriétaire de la base de données et certains membres munis de rôles d’administration peuvent modifier une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en supprimant une contrainte. Par défaut, seul le propriétaire de la table peut supprimer un index existant. Le succès ou l’échec de la fonction **DropIndex** ne dépend pas uniquement des droits d’accès de l’utilisateur de l’application, mais également du type d’index indiqué.  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Les consommateurs spécifient le nom d’index comme une chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pIndexID*. Le membre *eKind* de *pIndexID* doit être DBKIND_NAME. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client ne prend pas en charge la fonctionnalité de OLE DB de suppression de tous les index d’une table lorsque *pIndexID* a la valeur null. Si *pIndexID* a la valeur Null, E_INVALIDARG est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
