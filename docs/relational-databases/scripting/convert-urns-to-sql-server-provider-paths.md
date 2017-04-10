---
title: "Convertir des URN en chemins d&#39;acc&#232;s de fournisseur SQL&#160;Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Convertir des URN en chemins d&#39;acc&#232;s de fournisseur SQL&#160;Server
  Le modèle objet SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects) génère des URN (Uniform Resource Names) pour ses objets. Chaque URN identifie de façon unique un objet SMO et peut être converti en chemin de fournisseur PowerShell SQL Server à l’aide de l’applet de commande **Convert-UrnToPath**.  
  
## Conversion d'URN en chemins d'accès  
 Chaque URN a les mêmes informations qu'un chemin d'accès à l'objet, mais sous une forme différente. Voici, par exemple, le chemin d'accès à une table :  
  
 SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address  
  
 Et voici l'URN vers le même objet :  
  
 Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']  
  
 Si vous avez créé un objet SMO dans un script PowerShell, vous pouvez faire référence à la propriété **Urn** pour obtenir l’URN de l’objet, puis utiliser l’applet de commande **Convert-UrnToPath** pour convertir la chaîne URN SMO en chemin Windows PowerShell. Vous pouvez ensuite utiliser le fournisseur pour accéder à différents emplacements sur le chemin d'accès.  
  
 Si des noms de nœuds contiennent des caractères étendus qui ne sont pas pris en charge dans les noms de chemins Windows PowerShell, **Convert-UrnToPath** les encode dans leur représentation hexadécimale. Par exemple, « My:Table » est retourné sous la forme « My%3ATable ».  
  
 Pour obtenir des exemples d'utilisation de l'applet de commande, dans Windows PowerShell, exécutez :  
  
```  
Get-Help Convert-UrnToPath -Examples  
```  
  
## Voir aussi  
 [Expressions de requête et noms URN](../../powershell/query-expressions-and-uniform-resource-names.md)   
 [fournisseur PowerShell SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  