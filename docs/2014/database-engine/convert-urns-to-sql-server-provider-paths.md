---
title: Convertir des URN en chemins de fournisseur SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 77b6031e91f59fc691f0b1c055e90464d660d3a9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72797940"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a>Convertir des URN en chemins de fournisseur SQL Server
  Le modèle objet SMO ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects) génère des URN (Uniform Resource Names) pour ses objets. Chaque URN identifie de façon unique un objet SMO et peut être converti en chemin d'accès du fournisseur PowerShell SQL Server à l'aide de l'applet de commande `Convert-UrnToPath`.  
  
## <a name="converting-urns-to-paths"></a>Conversion d'URN en chemins d'accès  
 Chaque URN a les mêmes informations qu'un chemin d'accès à l'objet, mais sous une forme différente. Voici, par exemple, le chemin d'accès à une table :  
  
 SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address  
  
 Et voici l'URN vers le même objet :  
  
 Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']  
  
 Si vous avez créé un objet SMO dans un script PowerShell, vous pouvez référencer la propriété `Urn` pour obtenir l'URN de l'objet, puis utiliser l'applet de commande `Convert-UrnToPath` pour convertir la chaîne URN SMO en chemin d'accès Windows PowerShell. Vous pouvez ensuite utiliser le fournisseur pour accéder à différents emplacements sur le chemin d'accès.  
  
 Si des noms des nœuds contiennent des caractères étendus qui ne sont pas pris en charge dans les noms de chemins d'accès Windows PowerShell, `Convert-UrnToPath` les code dans leur représentation hexadécimale. Par exemple, « My:Table » est retourné sous la forme « My%3ATable ».  
  
 Pour obtenir des exemples d'utilisation de l'applet de commande, dans Windows PowerShell, exécutez :  
  
```powershell
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de requête et noms de ressource uniformes](../powershell/query-expressions-and-uniform-resource-names.md)   
 [Fournisseur SQL Server PowerShell](../powershell/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
