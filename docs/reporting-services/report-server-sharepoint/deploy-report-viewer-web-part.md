---
title: "Déployer le composant WebPart Visionneuse de rapports SQL Server Reporting Services sur un site SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a75ad193204e17e1d053aa4e00adba5f551d684b
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---

# <a name="deploy-the-sql-server-reporting-services-report-viewer-web-part-on-a-sharepoint-site"></a>Déployer le composant WebPart Visionneuse de rapports SQL Server Reporting Services sur un site SharePoint

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)])

Le composant WebPart Visionneuse de rapports est un composant WebPart personnalisé qui peut être utilisé pour afficher des rapports SQL Server Reporting Services (mode natif) au sein de votre site SharePoint. Vous pouvez utiliser le composant WebPart pour afficher, naviguer, imprimer et exporter des rapports sur un serveur de rapports. Le composant WebPart Visionneuse de rapports est associé à des fichiers de définition (.rdl) de rapport qui sont traitées par un serveur de rapports SQL Server Reporting Services ou un serveur de rapports Power BI. Ce composant WebPart Visionneuse de rapports ne peut pas être utilisé avec les rapports Power BI hébergés dans le serveur de rapports Power BI.

Utilisez les instructions suivantes pour déployer manuellement le package de solution qui ajoutent le composant WebPart Visionneuse de rapports dans un environnement SharePoint Server 2013 ou SharePoint Server 2016. Déploiement de la solution est une étape indispensable pour configurer le composant WebPart.

**Le composant WebPart Visionneuse de rapports est un package de solution autonome et n’est pas associé avec le mode intégré SharePoint pour SQL Server Reporting Services.**

## <a name="requirements"></a>Spécifications

**Prend en charge les versions de SharePoint Server :**  
* SharePoint Server 2016
* SharePoint Server 2013

**Prend en charge les versions de Reporting Services :**  
* SQL Server 2008 Reporting Services (mode natif) et versions ultérieures.
* Power BI Report Server

## <a name="download-the-report-viewer-web-part-solution-package"></a>Télécharger le package de solution partie de la visionneuse de rapports web

Le composant WebPart Visionneuse de rapports est disponible sur du Microsoft Download Center.

[Télécharger le package solution du composant WebPart Visionneuse de rapports](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="deploy-the-farm-solution"></a>Déployer la solution de batterie de serveurs

Cette section vous montre comment déployer le package de solution à votre batterie de serveurs SharePoint. Cette tâche ne doit être effectuée qu'une seule fois.

1. Sur un serveur SharePoint, ouvrez un SharePoint Management Shell à l’aide de la **exécuter en tant qu’administrateur** option.

2. Exécutez [Add-SPSolution](https://technet.microsoft.com/library/ff607552(v=office.16).aspx) pour ajouter la solution de batterie de serveurs.

    ```
    Add-SPSolution –LiteralPath "{path to file}\ReportViewerWebPart.wsp"
    ```

    L'applet de commande retourne le nom de la solution, son ID, et Deployed=False. À l'étape suivante, vous déploierez la solution.

3. Exécutez le [Install-SPSolution](https://technet.microsoft.com/library/ff607534(v=office.16).aspx) applet de commande pour déployer la solution de batterie de serveurs.

    **SharePoint 2013**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -CompatibilityLevel "14,15" -GACDeployment -WebApplication {URL to web application}
    ```

    **SharePoint 2016**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -GACDeployment -WebApplication {URL to web application}
    ```

## <a name="activate-feature"></a>Activer la fonctionnalité

1. Dans votre site SharePoint, sélectionnez le **ENGRENAGE** icône dans le coin supérieur gauche et sélectionnez **paramètres du Site*.

    ![Paramètres de site à partir de l’icône d’engrenage.](media/sharepoint-site-settings.png)

    Par défaut, les applications Web SharePoint sont accessibles via le port 80. Cela signifie que vous pouvez souvent accéder à un site SharePoint en entrant *http://<computer name>*  pour ouvrir la collection de sites racine.

3. Dans **Administration de Collection de sites**, sélectionnez **les fonctionnalités de collection de sites**.

4. Faites défiler vers le bas de la page jusqu'à ce que vous trouviez le **composant WebPart Visionneuse de rapports** fonctionnalité.

5. Sélectionnez **Activer**.

    ![Activer la fonctionnalité de composant WebPart Visionneuse de rapports](media/web-part-activiate-feature.png)

6. Répétez pour les collections de sites supplémentaires en ouvrant chaque site et en cliquant sur les Actions du Site.

Si vous le souhaitez, vous pouvez également utiliser PowerShell pour activer cette fonctionnalité sur tous les sites à l’aide de la [Enable-SPFeature](https://technet.microsoft.com/library/ff607803.aspx) applet de commande.

```
Get-SPWebApplication "<web application url>" | Get-SPSite -Limit ALL | 
        ForEach-Object {
            Write-Host "Enabling feature for $($_.URL)"
            Enable-SPFeature -identity "ReportViewerWebPart" -URL $_.URL -ErrorAction Continue
        }
```

## <a name="remove-the-solution"></a>Supprimer la solution

Bien que l’Administration centrale de SharePoint permette de retirer une solution, vous n’avez pas besoin de retirer le **ReportViewerWebPart.wsp** de fichiers, sauf si vous dépannez systématiquement un problème de déploiement d’installation ou un correctif.

1. Dans l’Administration centrale de SharePoint, dans **paramètres système**, sélectionnez **gérer les solutions de batterie de serveurs**.

2. Sélectionnez **ReportViewerWebPart.wsp**.

3. Sélectionnez retirer la Solution.

### <a name="remove-the-web-part-from-site-settings"></a>Supprimer le composant WebPart à partir des paramètres de Site

Retrait de la solution ne supprime pas le composant WebPart Visionneuse de rapports à partir de la liste des composants WebPart au sein de votre site SharePoint. Pour supprimer le composant WebPart Visionneuse de rapports, procédez comme suit.

1. Dans votre site SharePoint, sélectionnez le **ENGRENAGE** icône dans le coin supérieur gauche et sélectionnez **paramètres du Site*.

    ![Paramètres de site à partir de l’icône d’engrenage.](media/sharepoint-site-settings.png)

    Par défaut, les applications Web SharePoint sont accessibles via le port 80. Cela signifie que vous pouvez souvent accéder à un site SharePoint en entrant *http://<computer name>*  pour ouvrir la collection de sites racine.

2. Sous **galeries du Concepteur Web**, sélectionnez **WebPart**.

3. Sélectionnez le **icône de modification** regard **ReportViewerNativeMode.dwp**. Il peut ne pas figurer sur la première page de résultats.

4. Sélectionnez **supprimer l’élément**.

    ![Modifier et supprimer le composant WebPart en Mode natif de visionneuse de rapports](media/report-viewer-native-mode-edit-delete.png)

Tentative de suppression du composant WebPart à l’aide de PowerShell, mais il n’est pas une commande directe pour celle-ci. Pour obtenir un exemple de script, consultez [comment supprimer des composants WebPart de la galerie de composants WebPart](https://gallery.technet.microsoft.com/office/How-to-delete-Web-Parts-1132701f).

## <a name="supported-languages"></a>Langues prises en charge

Les langues suivantes sont prises en charge avec le composant WebPart :

* Anglais (en)
* Allemand (Allemagne)
* Espagnol (sp)
* Français (fr)
* Italien (it)
* Japonais (ja)
* Coréen (ko)
* Portugais (pt)
* Russe (ru)
* Chinois (simplifié - zh-HANS et zh-CHS)
* Chinois (traditionnel - zh-HANT et zh-CHT)

## <a name="next-steps"></a>Étapes suivantes

La visionneuse de rapports du composant WebPart a été déployé et l’activée, vous pouvez ajouter le composant WebPart à une page SharePoint. Pour plus d’informations, consultez [composant WebPart Visionneuse de rapports ajouter à une page SharePoint](add-report-viewer-web-part-to-page.md).

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
