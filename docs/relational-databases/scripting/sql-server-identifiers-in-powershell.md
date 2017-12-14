---
title: "Identificateurs SQL Server dans PowerShell | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: ssms
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- PowerShell [SQL Server], identifiers
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- identifiers [SQL Server], PowerShell
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 651099b0-33b4-453a-a864-b067f21eb8b9
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 95ead7b5686d23d3318d30b84abe868d00fb1622
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-identifiers-in-powershell"></a>Identificateurs SQL Server dans PowerShell
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour Windows PowerShell utilise les identificateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les chemins Windows PowerShell. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les identificateurs peuvent contenir des caractères que Windows PowerShell ne prend pas en charge dans les chemins. Vous devez placer ces caractères dans une séquence d’échappement ou leur appliquer un codage spécial lors de l’utilisation des identificateurs dans les chemins Windows PowerShell.  
  
## <a name="sql-server-identifiers-in-windows-powershell-paths"></a>Identificateurs SQL Server dans les chemins d'accès Windows PowerShell  
 Les fournisseurs Windows PowerShell présentent les hiérarchies de données à l'aide d'une structure de chemin d'accès semblable à celle utilisée pour le système de fichiers Windows. Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implémente les chemins d'accès aux objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)], le lecteur est défini sur SQLSERVER:, le premier dossier est défini sur \SQL et les objets de base de données sont référencés sous forme de conteneurs et d’éléments. Voici le chemin de la table Vendor dans le schéma Purchasing de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] dans une instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)]:  
  
```  
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les identificateurs sont les noms des objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tels que des noms de tables ou de colonnes. Il existe deux types d'identificateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Les identificateurs standard sont limités à un jeu des caractères qui sont également pris en charge dans les chemins d'accès Windows PowerShell. Ces noms peuvent être utilisés dans les chemins d'accès Windows PowerShell sans être modifiés.  
  
-   Les identificateurs délimités peuvent utiliser des caractères non pris en charge dans les noms de chemins d'accès Windows PowerShell. Ils sont appelés « identificateurs délimités » s'ils sont placés entre crochets et ([NomIdentificateur]) et « identificateurs entre guillemets » s'ils sont placés entre les guillemets ("NomIdentificateur"). Si un identificateur délimité utilise des caractères non pris en charge dans les chemins d'accès Windows PowerShell, les caractères doivent être codés ou placés dans une séquence d'échappement avant d'utiliser l'identificateur comme conteneur ou nom d'élément. L'encodage fonctionne pour tous les caractères. Certains caractères, comme les deux-points (:), ne peuvent pas être placés dans une séquence d'échappement.  
  
## <a name="sql-server-identifiers-in-cmdlets"></a>Identificateurs SQL Server dans les applets de commande  
 Certaines applets de commande [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiennent un paramètre dont l'entrée est un identificateur. Les valeurs de paramètres sont généralement fournies sous forme de constantes de chaîne entre guillemets ou dans des variables chaîne. Lorsque les identificateurs sont fournis sous forme de constantes de chaîne ou dans des variables, il n'y a aucun conflit avec l'ensemble des caractères pris en charge par Windows PowerShell.  
  
## <a name="sql-server-identifier-tasks"></a>Tâches des identificateurs SQL Server  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit comment spécifier un nom d'instance, y compris le nom de l'ordinateur sur lequel l'instance s'exécute.|[Spécifier des instances dans le fournisseur SQL Server PowerShell](../../relational-databases/scripting/specify-instances-in-the-sql-server-powershell-provider.md)|  
|Décrit comment spécifier le codage hexadécimal des caractères dans les identificateurs délimités qui ne sont pas pris en charge dans les chemins d'accès Windows PowerShell. Décrit également comment décoder les caractères hexadécimaux.|[Encoder et décoder des identificateurs SQL Server](../../relational-databases/scripting/encode-and-decode-sql-server-identifiers.md)|  
|Décrit comment utiliser le caractère d'échappement Windows PowerShell pour les caractères non pris en charge dans les chemins d'accès PowerShell.|[Placer des identificateurs SQL Server dans une séquence d'échappement](../../relational-databases/scripting/escape-sql-server-identifiers.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [fournisseur PowerShell SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
 [Identificateur de la base de données](../../relational-databases/databases/database-identifiers.md)  
  
  
