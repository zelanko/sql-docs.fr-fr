---
title: Suppression d’une étendue de procédure à partir de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: f04a0baa52eff0ac5742769e9eb6bfd7bfc246c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717527"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Suppression d'une procédure stockée étendue de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Pour supprimer chaque fonction de la procédure stockée étendue dans un défini par l’utilisateur étendu DLL de procédure stockée, un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrateur système doit exécuter la **sp_dropextendedproc** système procédure stockée, en spécifiant le nom de la fonction et le nom de la DLL dans laquelle cette fonction réside. Par exemple, cette commande supprime la fonction **xp_hello**, qui se trouve dans une DLL nommée xp_hello.dll, à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_dropextendedproc** ne supprime pas les procédures stockées étendues système. Au lieu de cela, l’administrateur système doit refuser l’autorisation EXECUTE sur la procédure stockée étendue à la **public** rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
