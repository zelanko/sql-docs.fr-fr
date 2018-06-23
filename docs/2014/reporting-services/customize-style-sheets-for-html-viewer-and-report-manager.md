---
title: Personnaliser des feuilles de Style pour la visionneuse HTML et le Gestionnaire de rapports | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- style sheets [Reporting Services]
ms.assetid: df805cff-b1de-4062-b2ac-423f37390fbd
caps.latest.revision: 18
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: b24525eff885b183b34f5810d79e44e4509e3f06
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039246"
---
# <a name="customize-style-sheets-for-html-viewer-and-report-manager"></a>Personnaliser des feuilles de style pour la visionneuse HTML et pour le Gestionnaire de rapports
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit de style en cascade par défaut des fichiers de feuilles (.css) qui définissent des styles pour le **rapport** barre d’outils dans la visionneuse HTML et pour le Gestionnaire de rapports. Si vous êtes un développeur Web expérimenté dans la création de feuilles de style en cascade, vous pouvez modifier les styles par défaut à vos propres risques pour changer les couleurs, les polices et la disposition de la barre d'outils ou du Gestionnaire de rapports. Ni les feuilles de style par défaut, ni les instructions pour modifier ces feuilles de style ne sont documentées dans cette version.  
  
 Toute modification incorrecte des feuilles de style peut entraîner des erreurs lors de l'ouverture des rapports. Si vous ne savez pas comment modifier des feuilles de style, il est recommandé d'utiliser les feuilles de style par défaut. Si vous choisissez de personnaliser les feuilles de style, veillez à créer une sauvegarde de tous les fichiers .css par défaut avant d'apporter des modifications.  
  
 La modification des feuilles de style n'a aucun effet sur l'aspect des rapports publiés que vous exécutez sur un serveur de rapports. Dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], les rapports ne font pas référence à des feuilles de style. Les rapports ad hoc qui sont générés automatiquement par le serveur de rapports utilisent des informations de style qui sont stockées sous forme de ressources incorporées dans les fichiers programmes du serveur de rapports. Les rapports que vous créez dans le Concepteur de rapports utilisent les polices, les couleurs et la mise en page que vous spécifiez dans la définition de rapport. Les styles sont créés en accord avec le reste de la mise en page.  
  
> [!NOTE]  
>  Si vous souhaitez utiliser des styles de rapport prédéfinis, utilisez l'Assistant Rapport pour créer un rapport. L'Assistant Rapport fournit différents thèmes que vous pouvez utiliser pour créer des rapports stylisés qui utilisent différentes combinaisons de couleurs et de polices. Les modèles de style qui définissent les thèmes d'un rapport peuvent être modifiés.  
  
## <a name="reporting-services-style-sheets"></a>Feuilles de style de Reporting Services  
 Le tableau suivant décrit les fichiers de feuille (.css) de style qui sont utilisés dans un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installation.  
  
|Feuille de style|Description|  
|-----------------|-----------------|  
|Htmlviewer.css|Est un exemple de feuille de style que vous pouvez utiliser comme modèle pour créer des styles personnalisés pour la barre d'outils **rapport** dans la visionneuse HTML.<br /><br /> Les styles par défaut utilisés par la visionneuse HTML sont compilés dans le serveur de rapports. Le fichier Htmlviewer.css constitue un exemple des styles que la visionneuse utilise.|  
|ReportingServices.css|Définit des styles pour le Gestionnaire de rapports.|  
  
> [!NOTE]  
>  Les feuilles de style suivantes sont utilisées pour la documentation en ligne du Gestionnaire de rapports et ne doivent jamais être modifiées : Sql.css et Mailto.css. D'autres feuilles de style définissent des styles pour les rapports et le Gestionnaire de rapports qui s'ouvrent dans des composants WebPart SharePoint. Ces feuilles de styles sont Rswebparts.css, Sp_full.css et Sp_small.css. La modification de ces feuilles de style n'est pas recommandée. Pour plus d’informations sur la façon dont les composants WebPart sont utilisées, consultez [afficher et Explorer Native Mode rapports à l’aide de composants WebPart SharePoint &#40;SSRS&#41;](reports/view-and-explore-native-mode-reports-using-sharepoint-web-parts-ssrs.md).  
  
## <a name="configuring-reporting-services-to-use-a-custom-style-sheet"></a>Configuration de Reporting Services pour l'utilisation d'une feuille de style personnalisée  
 La feuille de style doit être un fichier de feuille de style en cascade (.css) valide et doit se trouver dans le dossier Styles. Par défaut, le dossier Styles se trouve dans \< *lecteur*> : \Program Files\Microsoft SQL Server\MSSQL. *n*\Reporting Services\ReportServer\Styles.  
  
 Pour utiliser une feuille de style personnalisée pour la visionneuse HTML au moment de l'exécution, vous pouvez choisir une de ces approches :  
  
-   Ajouter le paramètre <`HTMLViewerStyleSheet`> au fichier de configuration [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   Spécifier la feuille de style sur une URL de rapport.  
  
### <a name="modifying-the-rsreportserverconfig-file"></a>Modification du fichier RSReportServer.config  
 Vous pouvez modifier le fichier RSReportServer.config pour spécifier une feuille de style personnalisée pour la visionneuse HTML. Le paramètre <`HTMLViewerStyleSheet`> n'est pas inclus dans le fichier par défaut. Vous devez le taper dans la sélection <`Configuration`> du fichier RSReportServer.config, puis spécifier la feuille de style que vous souhaitez utiliser. N'incluez pas l'extension .css lors de la spécification de la feuille de style.  
  
 L'exemple suivant montre comment spécifier la feuille de style :  
  
```  
<Configuration>  
...  
          <HTMLViewerStyleSheet>MyStyleSheet</HTMLViewerStyleSheet>  
...  
</Configuration>  
```  
  
### <a name="specifying-a-style-sheet-on-a-report-url"></a>Spécification d'une feuille de style sur une URL de rapport  
 Vous pouvez utiliser le paramètre d'accès URL `rc:StyleSheet` pour spécifier une feuille de style personnalisée sur l'URL de rapport. Pour plus d’informations sur la façon de spécifier les paramètres d’accès URL, consultez [référence de paramètre d’accès URL](url-access-parameter-reference.md).  
  
 L'exemple suivant montre comment ajouter des styles personnalisés :  
  
```  
http://localhost/reportserver?/AdventureWorksSampleReports/Product+Line+Sales&rs:Command=Render&rc:Stylesheet=MyStyleSheet  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Le Gestionnaire de rapports &#40;SSRS en Mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Visionneuse HTML et la barre d’outils rapport](html-viewer-and-the-report-toolbar.md)   
 [Fichier de Configuration RSReportServer](report-server/rsreportserver-config-configuration-file.md)  
  
  