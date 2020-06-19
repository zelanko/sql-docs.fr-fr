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
ms.openlocfilehash: 284da815de073248669da032c06ddeeb68c697a3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85027021"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Suppression d'une procédure stockée étendue de SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Pour supprimer chaque fonction de procédure stockée étendue dans une DLL de procédure stockée étendue définie par l’utilisateur, un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrateur système doit exécuter la procédure stockée système **sp_dropextendedproc** , en spécifiant le nom de la fonction et le nom de la dll dans laquelle cette fonction réside. Par exemple, cette commande supprime la fonction **xp_hello**, située dans une DLL nommée xp_hello.dll, à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , **sp_dropextendedproc** ne supprime pas les procédures stockées étendues du système. Au lieu de cela, l’administrateur système doit refuser l’autorisation EXECUTe sur la procédure stockée étendue au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
