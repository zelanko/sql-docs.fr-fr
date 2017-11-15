---
title: "Placer des identificateurs SQL Server dans une séquence d’échappement | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6bf78751fd46f1fdb4c8a4e99ff2f93f9abfdfd
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="escape-sql-server-identifiers"></a>Placer des identificateurs SQL Server dans une séquence d'échappement
  Vous pouvez souvent utiliser le caractère d'échappement Windows PowerShell « ` » (backtick) pour placer dans une séquence d'échappement les caractères qui sont autorisés dans les identificateurs délimités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mais pas les noms de chemins d'accès Windows PowerShell. Certains caractères ne peuvent toutefois pas être placés dans une séquence d'échappement. Par exemple, vous ne pouvez pas placés dans une séquence d'échappement le caractère deux-points (:) dans Windows PowerShell. Les identificateurs contenant ce caractère doivent être encodés. L'encodage est plus fiable que l'utilisation d'une séquence d'échappement, car l'encodage fonctionne pour tous les caractères.  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Le caractère ` (backtick) se trouve généralement sur une touche située dans la partie supérieure gauche du clavier, sous la touche Échap.  
  
## <a name="examples"></a>Exemples  
 Voici un exemple de séquence d'échappement pour le caractère # :  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 Voici un exemple de séquence d'échappement de la parenthèse lors de la spécification de (local) comme nom d'ordinateur :  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Identificateurs SQL Server dans PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [fournisseur PowerShell SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  
