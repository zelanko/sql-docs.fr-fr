---
title: Placer des identificateurs SQL Server dans une séquence d’échappement | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40897ed67ca661a763a2c654dc2c5fb223956264
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62672583"
---
# <a name="escape-sql-server-identifiers"></a>Placer des identificateurs SQL Server dans une séquence d'échappement
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Vous pouvez souvent utiliser le caractère d’échappement PowerShell « ` » (backtick) pour placer dans une séquence d’échappement les caractères qui sont autorisés dans les identificateurs délimités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], mais pas les noms de chemins Windows PowerShell. Certains caractères ne peuvent toutefois pas être placés dans une séquence d'échappement. Par exemple, vous ne pouvez pas placés dans une séquence d'échappement le caractère deux-points (:) dans Windows PowerShell. Les identificateurs contenant ce caractère doivent être encodés. L'encodage est plus fiable que l'utilisation d'une séquence d'échappement, car l'encodage fonctionne pour tous les caractères.  

> [!NOTE]
> Il existe deux modules SQL Server PowerShell : **SqlServer** et **SQLPS**. Le module **SQLPS** fait partie de l’installation de SQL Server (à des fins de compatibilité descendante), mais il n’est plus mis à jour. Le module PowerShell le plus récent est **SqlServer**. Le module **SqlServer** contient les versions mises à jour des applets de commande disponibles dans **SQLPS**, ainsi que de nouvelles applets de commande pour prendre en charge les dernières fonctionnalités SQL.
> Des versions précédentes du module **SqlServer** *étaient* fournies avec SQL Server Management Studio (SSMS), mais uniquement avec les versions 16.x de SSMS. Pour utiliser PowerShell avec SSMS 17.0 et ultérieur, vous devez installer le module **SqlServer** à partir de PowerShell Gallery.
> Pour installer le module **SqlServer**, consultez [Installer SQL Server PowerShell](download-sql-server-ps-module.md).

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
 [Identificateurs SQL Server dans PowerShell](sql-server-identifiers-in-powershell.md)   
 [fournisseur PowerShell SQL Server](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
