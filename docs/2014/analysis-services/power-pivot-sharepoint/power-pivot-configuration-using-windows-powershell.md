---
title: Configuration de PowerPivot à l’aide de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 4d83e53e-04f1-417d-9039-d9e81ae0483d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d3e0cdae7e9f57a7bfd62a3a0e947c43ced0b8c2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62749452"
---
# <a name="powerpivot-configuration-using-windows-powershell"></a>Configuration de PowerPivot à l'aide de Windows PowerShell
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] inclut des applets de commande Windows PowerShell que vous pouvez utiliser pour configurer une installation de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. La configuration complète d'une installation avec PowerShell requiert l'utilisation des applets de commande SharePoint et PowerPivot pour SharePoint. La majorité des configurations peut être effectuée avec un des outils de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Pour plus d'informations sur les outils, consultez [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).  
  
> [!IMPORTANT]  
>  Pour une batterie SharePoint 2010, SharePoint 2010 SP1 doit être installé avant de pouvoir configurer PowerPivot pour SharePoint, ou une batterie de serveurs SharePoint qui utilise un serveur de base de données [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] . Si vous n'avez pas encore installé le Service Pack, installez-le avant de commencer la configuration du serveur.  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-powershell"></a>Avantages de la configuration de PowerPivot pour SharePoint à l'aide de PowerShell  
 Générez des fichiers de script Windows PowerShell (.ps1) pour automatiser les tâches de configuration. Cette approche est recommandée si vous avez besoin d'une installation à base de script et d'étapes de configuration que vous pouvez exécuter sur n'importe quel serveur. Vous pouvez avoir besoin d'un tel script dans le cadre d'un plan de récupération d'urgence afin de reconstruire un serveur en cas de défaillance matérielle.  
  
## <a name="view-a-list-of-the-powerpivot-cmdlets-on-a-server"></a>Afficher une liste des applets de commande PowerPivot sur un serveur  
 Pour afficher le contenu et des exemples de la [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] applets de commande, consultez [PowerShell référence pour PowerPivot pour SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).  
  
 Pour utiliser PowerShell pour afficher une liste des applets de commande PowerPivot :  
  
1.  Ouvrez SharePoint Management Shell à l'aide de l'option **Exécuter en tant qu'administrateur** .  
  
2.  Entrez la commande suivante :  
  
    ```  
    Get-help *powerpivot*  
    ```  
  
     Vous devez voir une liste d'applets de commande dont le nom inclut PowerPivot. Par exemple, `Get-PowerPivotServiceApplication`. Le nombre d'applets de commande disponibles dépend de la version d'Analysis Services que vous utilisez.  
  
    -   10 applets de commande avec le serveur SQL Server 2012 SP1 Analysis Services configuré en mode SharePoint et SharePoint 2013. La version 2012 SP1 utilise une nouvelle architecture qui permet au serveur d'analyse de s'exécuter en dehors de la batterie de serveurs SharePoint et nécessite moins d'applets de commande de gestion Windows PowerShell.  
  
    -   17 applets de commande avec le serveur SQL Server 2012 Analysis Services configuré en mode SharePoint et SharePoint 2010.  
  
     Si aucune commande n’est retourné dans la liste ou vous voyez un message d’erreur semblable à «`get-help could not find *powerpivot* in a help file in this session.`», consultez la section suivante dans cette rubrique pour obtenir des instructions sur l’activation des applets de commande PowerPivot sur le serveur.  
  
     Toutes les applets de commande intègrent un système d'aide en ligne. L'exemple suivant montre comment afficher l'aide en ligne pour l'applet de commande `New-PowerPivotServiceApplication` :  
  
    ```  
    Get-help new-powerpivotserviceapplication -full  
    ```  
  
     Sinon, pour afficher uniquement les exemples, utilisez la syntaxe suivante :  
  
    ```  
    Get-help new-powerpivotserviceapplication -example  
    ```  
  
## <a name="enable-powerpivot-cmdlets-on-a-server"></a>Activer les applets de commande PowerPivot sur un serveur  
 Les applets de commande PowerPivot sont disponibles après que vous avez installé PowerPivot pour SharePoint et déployer la solution de batterie de serveurs. Les solutions sont déployées lorsque vous appelez l'outil de configuration PowerPivot. Suivez ces étapes pour pouvoir utiliser des applets de commande :  
  
1.  Ouvrez SharePoint Management Shell à l'aide de l'option **Exécuter en tant qu'administrateur** .  
  
2.  Exécutez la première applet de commande :  
  
    ```  
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     L'applet de commande retourne le nom de la solution, son ID, et Deployed=False. À l'étape suivante, vous déployez la solution.  
  
3.  Exécutez la deuxième applet de commande pour déployer la solution :  
  
    ```  
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
4.  Fermez la fenêtre. Rouvrez-la, à nouveau à l'aide de l'option **Exécuter en tant qu'administrateur** .  
  
## <a name="related-content"></a>Contenu associé  
 [Administration et configuration d’un serveur PowerPivot dans l’Administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [Outils de configuration de PowerPivot](power-pivot-configuration-tools.md)  
  
 [Référence PowerShell pour PowerPivot pour SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
  
