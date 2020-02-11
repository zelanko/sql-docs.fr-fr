---
title: Déployer des solutions PowerPivot sur SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f202a2b7-34e0-43aa-90d5-c9a085a37c32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c91225761c76a58b81d8895698ca059014969f0f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72782830"
---
# <a name="deploy-powerpivot-solutions-to-sharepoint"></a>Déployer des solutions PowerPivot sur SharePoint
  Utilisez les instructions suivantes pour déployer manuellement deux packages de solution qui ajoutent des fonctionnalités PowerPivot à un environnement SharePoint Server 2010. Le déploiement des solutions est une étape indispensable pour configurer PowerPivot pour SharePoint sur un serveur SharePoint 2010. Pour afficher la liste complète des étapes requises, consultez [administration et configuration du serveur PowerPivot dans l’administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
 Pour déployer les solutions, vous pouvez également utiliser l'outil de configuration PowerPivot. L'utilisation de l'outil de configuration est plus simple et plus efficace pour une installation sur un serveur unique, mais vous souhaiterez peut-être recourir à l'Administration centrale et à PowerShell si vous préférez travailler avec un outil qui vous est familier ou si vous configurez plusieurs fonctionnalités en même temps. Pour plus d’informations sur l’utilisation de l’outil de configuration de, consultez [outils de configuration de PowerPivot](power-pivot-configuration-tools.md).  
  
 Avant de déployer ces solutions, vous devez d'abord installer PowerPivot pour SharePoint à l'aide du support d'installation de SQL Server 2012. Le programme d'installation de SQL Server installe les packages de solution que vous êtes sur le point de déployer.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Condition préalable : vérifier que l’application Web utilise l’authentification en mode classique](#bkmk_classic)  
  
 [Étape 1 : déployer la solution de batterie de serveurs](#bkmk_farm)  
  
 [Étape 2 : déployer la solution d'application Web PowerPivot sur l'Administration centrale](#deployCA)  
  
 [Étape 3 : déployer la solution d'application Web PowerPivot sur d'autres applications Web](#deployUI)  
  
 [Redéployer ou retirer la solution](#retract)  
  
 [À propos des solutions PowerPivot](#intro)  
  
##  <a name="bkmk_classic"></a>Condition préalable : vérifier que l’application Web utilise l’authentification en mode classique  
 PowerPivot pour SharePoint n'est pris en charge que pour les applications Web qui utilisent l'authentification en mode classique. Pour vérifier si l’application utilise le mode classique, exécutez l’applet de commande PowerShell suivante à partir de **SharePoint 2010 Management Shell**, en remplaçant `http://<top-level site name>` par le nom de votre site SharePoint :  
  
```powershell
Get-SPWebApplication http://<top-level site name> | Format-List UseClaimsAuthentication  
```  
  
 La valeur de retour devrait être **False**. Si la **valeur est true**, vous ne pouvez pas accéder aux données PowerPivot avec cette application Web.  
  
##  <a name="bkmk_farm"></a>Étape 1 : déployer la solution de batterie de serveurs  
 Cette section montre comment déployer des solutions à l'aide de PowerShell, mais vous pouvez également utiliser l'outil de configuration PowerPivot pour effectuer cette tâche. Pour plus d’informations, consultez [configurer ou réparer PowerPivot pour SharePoint 2010 &#40;outil de configuration de PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md).  
  
 Cette tâche ne doit être effectuée qu'une seule fois, après l'installation de PowerPivot pour SharePoint.  
  
1.  Sur un serveur disposant d’une installation de PowerPivot pour SharePoint, ouvrez un environnement de gestion SharePoint 2010 à l’aide de l’option **exécuter en tant qu’administrateur** .  
  
2.  Exécutez l'applet de commande suivante pour ajouter la solution de batterie de serveurs.  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     L'applet de commande retourne le nom de la solution, son ID, et Deployed=False. À l'étape suivante, vous déploierez la solution.  
  
3.  Exécutez l'applet de commande suivante pour déployer la solution de batterie de serveurs :  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
##  <a name="deployCA"></a>Étape 2 : déployer la solution d’application Web PowerPivot dans l’administration centrale  
 Après avoir déployé la solution de batterie de serveurs, vous devez déployer la solution d'application Web sur l'Administration centrale. Cette étape ajoute le tableau de bord de gestion PowerPivot dans l'Administration centrale.  
  
1.  Ouvrez SharePoint 2010 Management Shell à l'aide de l'option **Exécuter en tant qu'administrateur** .  
  
2.  Exécutez l'applet de commande suivante pour créer une référence à l'Administration centrale :  
  
    ```powershell
    $centralAdmin = $(Get-SPWebApplication -IncludeCentralAdministration | Where { $_.IsAdministrationWebApplication -eq $TRUE})  
    ```  
  
3.  Exécutez l'applet de commande suivante pour ajouter la solution de batterie de serveurs.  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotWebApp.wsp"  
    ```  
  
     L'applet de commande retourne le nom de la solution, son ID, et Deployed=False. À l'étape suivante, vous déploierez la solution.  
  
4.  Exécutez l'applet de commande suivante pour installer la solution d'application Web sur l'Administration centrale.  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotWebApp.wsp -GACDeployment -Force -WebApplication $centralAdmin  
    ```  
  
 Maintenant que la solution d'application Web est déployée sur l'Administration centrale, vous pouvez recourir à cette dernière pour effectuer toutes les étapes de configuration restantes.  
  
##  <a name="deployUI"></a>Étape 3 : déployer la solution d’application Web PowerPivot sur d’autres applications Web  
 Dans la tâche précédente, vous avez déployé Powerpivotwebapp.wsp sur l'Administration centrale. Dans cette section, vous allez déployer powerpivotwebapp.wsp sur chaque application Web existante qui prend en charge l'accès aux données PowerPivot. Si vous ajoutez des applications Web supplémentaires par la suite, assurez-vous que vous répétez cette étape pour chacune de ces applications.  
  
1.  Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les solutions de la batterie**.  
  
2.  Cliquez sur **powerpivotwebapp.wsp**.  
  
3.  Cliquez sur **Déployer la solution**.  
  
4.  Dans **déployer sur ?**, sélectionnez l’application Web SharePoint pour laquelle vous souhaitez ajouter la prise en charge des fonctionnalités PowerPivot.  
  
5.  Cliquez sur **OK**.  
  
6.  Répétez ces opérations pour les autres applications Web SharePoint qui prendront également en charge l'accès aux données PowerPivot.  
  
##  <a name="retract"></a>Redéployer ou retirer la solution  
 Bien que l'Administration centrale de SharePoint permette de retirer une solution, vous n'avez pas besoin de retirer le fichier powerpivotwebapp.wsp, sauf si vous dépannez une installation de manière systématique ou si vous corrigez un problème de déploiement.  
  
1.  Dans l'Administration centrale de SharePoint 2010, sous Paramètres système, cliquez sur **Gérer les solutions de la batterie**.  
  
2.  Cliquez sur **powerpivotwebapp. wsp**.  
  
3.  Cliquez sur **Retirer la solution**.  
  
 Si vous rencontrez des problèmes de déploiement de serveur que vous suivez dans la solution de batterie de serveurs, vous pouvez le redéployer en exécutant l’option **réparer** dans l’outil de configuration de PowerPivot. Il est préférable de réparer les opérations via l'outil, car vous aurez moins d'étapes à effectuer. Pour plus d’informations, consultez [configurer ou réparer PowerPivot pour SharePoint 2010 &#40;outil de configuration de PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md).  
  
 Si vous souhaitez néanmoins redéployer toutes les solutions, veillez à le faire dans cet ordre :  
  
1.  Retirez la solution d'application Web PowerPivot de toutes les applications Web SharePoint qui l'utilisent.  
  
2.  Retirez la solution de batterie PowerPivot.  
  
3.  Redéployez la solution de batterie PowerPivot.  
  
4.  Redéployez la solution d'application Web PowerPivot sur toutes les applications Web SharePoint.  
  
##  <a name="intro"></a>À propos des solutions PowerPivot  
 PowerPivot pour SharePoint utilise deux packages de solution pour déployer ses fichiers programme et ses pages d'application dans la batterie de serveurs et dans des applications Web individuelles.  
  
-   La solution de batterie est globale. Elle est déployée une fois, puis reste automatiquement à la disposition des nouveaux serveurs PowerPivot pour SharePoint que vous ajouterez ultérieurement à la batterie.  
  
-   La solution d'application Web est spécifique aux applications et doit être déployée sur chaque application Web de la batterie de serveurs, notamment sur l'application Web Administration centrale.  
  
 Chaque solution est déployée différemment.  La solution de batterie de serveurs est déployée une fois, après l'installation de la première instance de PowerPivot pour SharePoint. Pour déployer la solution de batterie de serveurs, utilisez l'outil de configuration PowerPivot ou les applets de commande PowerShell.  
  
 La solution d'application Web est d'abord déployée sur l'Administration centrale, puis sur d'autres applications Web qui prendront en charge les demandes de données PowerPivot. Pour déployer la solution d'application Web sur l'Administration centrale, vous devez utiliser l'outil de configuration PowerPivot ou l'applet de commande PowerShell. Pour toutes les autres applications Web, vous pouvez déployer la solution d'application Web manuellement à l'aide de l'Administration centrale ou de PowerShell.  
  
|Solution|Description|  
|--------------|-----------------|  
|Powerpivotfarm.wsp|Ajoute Microsoft.AnalysisServices.SharePoint.Integration.dll à l'assembly global.<br /><br /> Ajoute Microsoft.AnalysisServices.ChannelTransport.dll à l'assembly global.<br /><br /> Installe des fonctionnalités et des fichiers de ressources, et enregistre des types de contenu.<br /><br /> Ajoute des modèles de bibliothèque pour la bibliothèque Galerie PowerPivot et les bibliothèques de Flux de données.<br /><br /> Des pages d'application sont ajoutées pour la configuration de l'application de service, le Tableau de bord de gestion PowerPivot, l'actualisation des données et la bibliothèque Galerie PowerPivot.|  
|powerpivotwebapp.wsp|Ajoute les fichiers de ressources Microsoft.AnalysisServices.SharePoint.Integration.dll au dossier des extensions du serveur Web sur le Web frontal.<br /><br /> Ajoute le service Web PowerPivot sur le Web frontal.<br /><br /> Ajoute la génération de miniatures pour la bibliothèque Galerie PowerPivot.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à niveau PowerPivot pour SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Administration et configuration du serveur PowerPivot dans l’administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Configuration de PowerPivot à l'aide de Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
