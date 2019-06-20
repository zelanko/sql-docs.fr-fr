---
title: Référence de PowerShell pour Analysis Services Power Pivot pour SharePoint | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9228eb879ed1417b31c95d53783d32acf53bcdb4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62509805"
---
# <a name="powershell-reference-for-power-pivot-for-sharepoint"></a>Référence PowerShell pour Power Pivot pour SharePoint
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Cette section répertorie les applets de commande PowerShell utilisées pour configurer ou gérer une installation [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Pour plus d’informations sur l’activation des applets de commande et l’affichage de l’aide intégrée, consultez [Configuration de Power Pivot à l’aide de Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md).  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
## <a name="cmdlet-list"></a>Liste des applets de commande  
 Pour afficher la liste des applets de commande à partir de l’invite PowerShell :  
  
1.  Ouvrez SharePoint Management Shell à l'aide de l'option **Exécuter en tant qu'administrateur** .  
  
2.  Entrez la commande suivante : `Get-help *powerpivot*`  
  
|Applet de commande|Versions prises en charge|  
|------------|------------------------|  
|[Get-PowerPivotServiceApplication, applet de commande](../../analysis-services/powershell/get-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Applet de commande Get-PowerPivotSystemService](../../analysis-services/powershell/get-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Applet de commande Get-PowerPivotSystemServiceInstance](../../analysis-services/powershell/get-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Applet de commande New-PowerPivotServiceApplication](../../analysis-services/powershell/new-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[New-PowerPivotSystemServiceInstance, applet de commande](../../analysis-services/powershell/new-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Applet de commande Remove-PowerPivotServiceApplication](../../analysis-services/powershell/remove-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Applet de commande Remove-PowerPivotSystemServiceInstance](../../analysis-services/powershell/remove-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotServiceApplication, applet de commande](../../analysis-services/powershell/set-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotSystemService, applet de commande](../../analysis-services/powershell/set-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Applet de commande Update-PowerPivotSystemService](../../analysis-services/powershell/update-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
  
 Remarque : Les applets de commande suivantes ne fonctionnent qu’avec SharePoint 2010, qui [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ne prend pas en charge.  
  
-   Get-PowerPivotEngineService  
  
-   Get-PowerPivotEngineServiceInstance  
  
-   New-PowerPivotEngineServiceInstance  
  
-   Remove-PowerPivotEngineServiceInstance  
  
-   Set-PowerPivotEngineService  
  
-   Set-PowerPivotEngineServiceInstance  
  
-   Update-PowerPivotEngineService  
  
  
