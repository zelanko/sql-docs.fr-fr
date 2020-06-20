---
title: Placer des identificateurs SQL Server dans une séquence d’échappement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: a2b7d37e20aae20b548da83fbd32858e8192d3ae
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960429"
---
# <a name="escape-sql-server-identifiers"></a>Placer des identificateurs SQL Server dans une séquence d'échappement
  Vous pouvez souvent utiliser le caractère d'échappement Windows PowerShell « ` » (backtick) pour placer dans une séquence d'échappement les caractères qui sont autorisés dans les identificateurs délimités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , mais pas les noms de chemins d'accès Windows PowerShell. Certains caractères ne peuvent toutefois pas être placés dans une séquence d'échappement. Par exemple, vous ne pouvez pas placés dans une séquence d'échappement le caractère deux-points (:) dans Windows PowerShell. Les identificateurs contenant ce caractère doivent être encodés. L'encodage est plus fiable que l'utilisation d'une séquence d'échappement, car l'encodage fonctionne pour tous les caractères.  
  
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
 [Identificateurs de SQL Server dans PowerShell](sql-server-identifiers-in-powershell.md)   
 [Fournisseur SQL Server PowerShell](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
