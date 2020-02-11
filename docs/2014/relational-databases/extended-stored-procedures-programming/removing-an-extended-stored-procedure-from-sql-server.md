---
title: Suppression d’une procédure stockée étendue de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bcb58ac180861641803147d1dfea621bd52df9a6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62512024"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Suppression d'une procédure stockée étendue de SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Pour supprimer chaque fonction de procédure stockée étendue dans une DLL de procédure stockée étendue définie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par l’utilisateur, un administrateur système doit exécuter la procédure stockée système **sp_dropextendedproc** , en spécifiant le nom de la fonction et le nom de la dll dans laquelle cette fonction réside. Par exemple, cette commande supprime la fonction **xp_hello**, située dans une dll nommée xp_hello. dll, à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]partir de :  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 À partir [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]de, **sp_dropextendedproc** ne supprime pas les procédures stockées étendues du système. Au lieu de cela, l’administrateur système doit refuser l’autorisation EXECUTe sur la procédure stockée étendue au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
