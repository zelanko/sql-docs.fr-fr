---
title: "Placer des identificateurs SQL&#160;Server dans une s&#233;quence d&#39;&#233;chappement | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Placer des identificateurs SQL&#160;Server dans une s&#233;quence d&#39;&#233;chappement
  Vous pouvez souvent utiliser le caractère d'échappement Windows PowerShell « ` » (backtick) pour placer dans une séquence d'échappement les caractères qui sont autorisés dans les identificateurs délimités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais pas les noms de chemins d'accès Windows PowerShell. Certains caractères ne peuvent toutefois pas être placés dans une séquence d'échappement. Par exemple, vous ne pouvez pas placés dans une séquence d'échappement le caractère deux-points (:) dans Windows PowerShell. Les identificateurs contenant ce caractère doivent être encodés. L'encodage est plus fiable que l'utilisation d'une séquence d'échappement, car l'encodage fonctionne pour tous les caractères.  
  
## Avant de commencer  
 Le caractère ` (backtick) se trouve généralement sur une touche située dans la partie supérieure gauche du clavier, sous la touche Échap.  
  
## Exemples  
 Voici un exemple de séquence d'échappement pour le caractère # :  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 Voici un exemple de séquence d'échappement de la parenthèse lors de la spécification de (local) comme nom d'ordinateur :  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## Voir aussi  
 [Identificateurs SQL Server dans PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [fournisseur PowerShell SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  