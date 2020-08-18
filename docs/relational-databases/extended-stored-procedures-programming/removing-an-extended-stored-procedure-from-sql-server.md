---
description: Suppression d'une procédure stockée étendue de SQL Server
title: Suppression d’une procédure stockée étendue
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
ms.custom: seo-dt-2019
ms.openlocfilehash: d7296391a9105c9831ed8652f7b63e234ac4f6df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460761"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Suppression d'une procédure stockée étendue de SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Pour supprimer chaque fonction de procédure stockée étendue dans une DLL de procédure stockée étendue définie par l’utilisateur, un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrateur système doit exécuter la procédure stockée système **sp_dropextendedproc** , en spécifiant le nom de la fonction et le nom de la dll dans laquelle cette fonction réside. Par exemple, cette commande supprime la fonction **xp_hello**, située dans une DLL nommée xp_hello.dll, à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , **sp_dropextendedproc** ne supprime pas les procédures stockées étendues du système. Au lieu de cela, l’administrateur système doit refuser l’autorisation EXECUTe sur la procédure stockée étendue au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
