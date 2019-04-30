---
title: Installation du Conseiller de mise à niveau à partir de l’invite de commandes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- command prompt [Upgrade Advisor]
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: a6841cc2-ca13-4b1c-9343-9e4d54312c3a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df68b9ee1e778d0523b63d69bd010022b6f6f219
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301338"
---
# <a name="installing-upgrade-advisor-from-the-command-prompt"></a>Installation du Conseiller de mise à niveau à partir de l'invite de commandes
  Vous pouvez installer le Conseiller de mise à niveau à l'aide de l'Assistant Installation ou à partir de l'invite de commandes. L'invite de commandes vous permet d'effectuer des installations automatisées et sans assistance.  
  
## <a name="installation-syntax"></a>Syntaxe d'installation  
 La syntaxe de base pour installer le Conseiller de mise à niveau à partir de l'invite de commandes est la suivante :  
  
 `SQLUA.msi [options]`  
  
 Le tableau suivant affiche les options les plus courantes.  
  
|Argument|Description|  
|--------------|-----------------|  
|/q[n&#124;b&#124;r&#124;f]|Définit le niveau de l'interface utilisateur (UI) :<br /><br /> n = aucune interface utilisateur<br /><br /> b = interface utilisateur de base (progression uniquement, aucune invite)<br /><br /> r = interface utilisateur réduite (boîte de dialogue à la fin de l'installation)<br /><br /> f = interface utilisateur complète|  
|/L|Spécifie les options du fichier journal. Pour enregistrer tous les messages dans *nom_fichier_journal*, utilisez **-L\*v**_nom_fichier_journal_. Pour enregistrer uniquement les messages d’erreur, utilisez `-Le` *nom_fichier_journal*.|  
|ADDLOCAL=ALL&#124; REMOVE=ALL&#124;REINSTALL=ALL|Spécifie que le Conseiller de mise à niveau doit être installé (ADDLOCAL), supprimé (REMOVE) ou réinstallé (REINSTALL).|  
|UAINSTALLDIR=path|Installe le Conseiller de mise à niveau à l'emplacement spécifié par le chemin d'accès.|  
  
## <a name="installation-examples"></a>Exemples d'installation  
 L'exemple suivant indique comment installer le Conseiller de mise à niveau à l'aide de l'invite de commandes :  
  
```  
SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 Vous pouvez également utiliser le programme Msiexec lorsque vous exécutez cette commande :  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 Cela peut s'avérer utile si vous devez utiliser des options d'installation supplémentaires.  
  
## <a name="removal-examples"></a>Exemples de suppression  
 L'exemple suivant indique comment supprimer le Conseiller de mise à niveau à l'aide de l'invite de commandes :  
  
```  
SQLUA.msi /qn REMOVE=ALL  
```  
  
 Vous pouvez également utiliser le programme Msiexec lorsque vous exécutez cette commande :  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn REMOVE=ALL  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Installation du Conseiller de mise à niveau](../../../2014/sql-server/install/installing-upgrade-advisor.md)   
 [Prérequis pour le Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
