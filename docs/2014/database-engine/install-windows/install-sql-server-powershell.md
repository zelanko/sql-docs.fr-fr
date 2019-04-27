---
title: Installer SQL Server PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a90a30a0ae7fe09d49b1d42b577b13370c48c0de
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62775439"
---
# <a name="install-sql-server-powershell"></a>Installer SQL Server PowerShell
  Le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'arrête s'il détecte que vous avez sélectionné des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui incluent des composants PowerShell, alors que Windows PowerShell 2.0 n'est pas installé. Vous devez installer PowerShell à l'aide de Windows Management Framework, puis réexécuter l'installation.  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-powershell-support"></a>Installation de la prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell  
 Vous installez le logiciel qui fournit la prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour Windows PowerShell à l'aide du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Lorsque vous sélectionnez des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui requièrent la prise en charge de PowerShell, le programme d'installation vérifie que Windows PowerShell 2.0 est installé. Si PowerShell 2.0 est présent, le programme d'installation installe ensuite les composants suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell :  
  
-   Les composants logiciels enfichables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell. Les composants logiciels enfichables sont des fichiers DLL qui implémentent deux types de prises en charge de Windows PowerShell pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   Un jeu d'applets de commande [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les applets de commande sont des commandes qui implémentent une action spécifique. Par exemple, **Invoke-Sqlcmd** exécute un script [!INCLUDE[tsql](../../includes/tsql-md.md)] ou XQuery qui peut également être exécuté à l’aide de l’utilitaire **sqlcmd** , et **Invoke-PolicyEvaluation** indique si les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont conformes aux stratégies de la gestion basée sur des stratégies.  
  
    -   Un fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le fournisseur vous permet de naviguer dans la hiérarchie d'objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant un chemin d'accès semblable à un chemin d'accès de système de fichiers. Chaque objet est associé à une classe des modèles objets de gestion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez utiliser les méthodes et propriétés de la classe pour effectuer des travaux sur les objets. Par exemple, si vous changez de répertoire (cd) pour accéder à un objet de bases de données dans un chemin d'accès, vous pouvez utiliser les méthodes et propriétés de la classe Microsoft.SqlServer.Managment.SMO.Database pour gérer la base de données.  
  
-   Le **sqlps** module est importé dans les sessions Windows PowerShell 2.0 pour charger le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enfichables.  
  
-   Déconseillées **sqlps** utilitaire qui démarre une session Windows PowerShell 2.0 et importe le **sqlps** module.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] prend en charge le démarrage de sessions Windows PowerShell à partir de l’arborescence de l’Explorateur d’objets. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prend en charge les étapes de travail Windows PowerShell.  
  
 Si Windows PowerShell 2.0 n’a pas été installé ou a été désinstallé, vous devez l’installer en suivant les instructions la [Windows Management Framework](https://go.microsoft.com/fwlink/?LinkId=186214) page.  
  
 Si Windows PowerShell est désinstallé au terme de la procédure d'installation, les fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour Windows PowerShell ne s'exécutent pas. Windows PowerShell peut être désinstallé par les utilisateurs Windows, et il peut être nécessaire de désinstaller Windows PowerShell pour certaines mises à niveau du système d'exploitation Windows. Pour utiliser les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, vous devez réinstaller PowerShell 2.0 à l'aide de Windows Management Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)  
  
  
