---
title: Personnaliser des feuilles de style pour la visionneuse HTML et la Gestionnaire de rapports | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 04/26/2019
ms.openlocfilehash: 7c7745d69e234f81c2a331d214789e93e9fd4014
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "64568268"
---
# <a name="customize-style-sheets-for-html-viewer-and-report-manager"></a>Personnaliser des feuilles de style pour la visionneuse HTML et pour le Gestionnaire de rapports
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]fournit des fichiers de feuilles de style en cascade (. CSS) par défaut qui définissent des styles pour la barre d’outils **rapport** dans la visionneuse HTML et pour gestionnaire de rapports. Si vous êtes un développeur Web expérimenté dans la création de feuilles de style en cascade, vous pouvez modifier les styles par défaut à vos propres risques pour changer les couleurs, les polices et la disposition de la barre d'outils ou du Gestionnaire de rapports. Ni les feuilles de style par défaut, ni les instructions pour modifier ces feuilles de style ne sont documentées dans cette version.  
  
 Toute modification incorrecte des feuilles de style peut entraîner des erreurs lors de l'ouverture des rapports. Si vous ne savez pas comment modifier des feuilles de style, il est recommandé d'utiliser les feuilles de style par défaut. Si vous choisissez de personnaliser les feuilles de style, veillez à créer une sauvegarde de tous les fichiers .css par défaut avant d'apporter des modifications.  
  
 La modification des feuilles de style n'a aucun effet sur l'aspect des rapports publiés que vous exécutez sur un serveur de rapports. Dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], les rapports ne font pas référence à des feuilles de style. Les rapports ad hoc qui sont générés automatiquement par le serveur de rapports utilisent des informations de style qui sont stockées sous forme de ressources incorporées dans les fichiers programmes du serveur de rapports. Les rapports que vous créez dans le Concepteur de rapports utilisent les polices, les couleurs et la mise en page que vous spécifiez dans la définition de rapport. Les styles sont créés en accord avec le reste de la mise en page.  
  
> [!NOTE]  
>  Si vous souhaitez utiliser des styles de rapport prédéfinis, utilisez l'Assistant Rapport pour créer un rapport. L'Assistant Rapport fournit différents thèmes que vous pouvez utiliser pour créer des rapports stylisés qui utilisent différentes combinaisons de couleurs et de polices. Les modèles de style qui définissent les thèmes d'un rapport peuvent être modifiés.  
  
## <a name="reporting-services-style-sheets"></a>Feuilles de style de Reporting Services  
 Le tableau suivant décrit les fichiers de feuilles de style (.css) qui sont utilisés dans une installation [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
|Feuille de style|Description|  
|-----------------|-----------------|  
|Htmlviewer.css|Est un exemple de feuille de style que vous pouvez utiliser comme modèle pour créer des styles personnalisés pour la barre d'outils **rapport** dans la visionneuse HTML.<br /><br /> Les styles par défaut utilisés par la visionneuse HTML sont compilés dans le serveur de rapports. Le fichier Htmlviewer.css constitue un exemple des styles que la visionneuse utilise.|  
|ReportingServices.css|Définit des styles pour le Gestionnaire de rapports.|  
  
## <a name="configuring-reporting-services-to-use-a-custom-style-sheet"></a>Configuration de Reporting Services pour l'utilisation d'une feuille de style personnalisée  
 La feuille de style doit être un fichier de feuille de style en cascade (.css) valide et doit se trouver dans le dossier Styles. Par défaut, le dossier styles se trouve dans \<le *lecteur*> : \Program Files\Microsoft SQL Server\MSSQL. *n*\Reporting Services\ReportServer\styles.  
  
 Pour utiliser une feuille de style personnalisée pour la visionneuse HTML au moment de l'exécution, vous pouvez choisir une de ces approches :  
  
-   Ajoutez le paramètre `HTMLViewerStyleSheet` de> <au [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fichier de configuration.  
  
-   Spécifier la feuille de style sur une URL de rapport.  
  
### <a name="modifying-the-rsreportserverconfig-file"></a>Modification du fichier RSReportServer.config  
 Vous pouvez modifier le fichier RSReportServer.config pour spécifier une feuille de style personnalisée pour la visionneuse HTML. Le paramètre `HTMLViewerStyleSheet` <> n’est pas inclus dans le fichier par défaut. Vous devez le taper dans le <`Configuration`> sélection du fichier RSReportServer. config, puis spécifier la feuille de style que vous souhaitez utiliser. N'incluez pas l'extension .css lors de la spécification de la feuille de style.  
  
 L'exemple suivant montre comment spécifier la feuille de style :  
  
```  
<Configuration>  
...  
          <HTMLViewerStyleSheet>MyStyleSheet</HTMLViewerStyleSheet>  
...  
</Configuration>  
```  
  
### <a name="specifying-a-style-sheet-on-a-report-url"></a>Spécification d'une feuille de style sur une URL de rapport  
 Vous pouvez utiliser le paramètre d'accès URL `rc:StyleSheet` pour spécifier une feuille de style personnalisée sur l'URL de rapport. Pour plus d’informations sur la spécification des paramètres d’accès URL, consultez [référence de paramètre d’accès URL](url-access-parameter-reference.md).  
  
 L'exemple suivant montre comment ajouter des styles personnalisés :  
  
```  
http://localhost/reportserver?/AdventureWorksSampleReports/Product+Line+Sales&rs:Command=Render&rc:Stylesheet=MyStyleSheet  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Visionneuse HTML et barre d’outils rapport](html-viewer-and-the-report-toolbar.md)   
 [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)  
  
  
