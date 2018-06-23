---
title: Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuration options [Reporting Services]
- DeviceInfo settings
- rendering extensions [Reporting Services], overriding behaviors
- parameters [Reporting Services], report rendering
- overriding report rendering behavior
- extensions [Reporting Services], rendering
ms.assetid: 3bf7ab2b-70bb-41c8-acda-227994d15aed
caps.latest.revision: 31
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 201a3af8cfd9acad20539327f4dc9afbfcb2a435
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043093"
---
# <a name="customize-rendering-extension-parameters-in-rsreportserverconfig"></a>Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config
  Vous pouvez spécifier des paramètres d'extension de rendu dans le fichier de configuration RSReportServer afin de remplacer le comportement de la génération de rapport par défaut pour les rapports exécutés sur un serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Vous pouvez modifier les paramètres d'extension de rendu pour obtenir les résultats suivants :  
  
-   modifier l'affichage du nom de l'extension de rendu dans la liste Exporter de la barre d'outils Rapport (par exemple, pour remplacer « Web archive » par « MHTML »), ou localiser le nom dans une autre langue ;  
  
-   créer plusieurs instances de la même extension de rendu afin de gérer différentes options de présentation de rapport (par exemple, une version en mode Portrait et Paysage de l'extension de rendu Image) ;  
  
-   modifier les paramètres d'extension de rendu par défaut afin d'utiliser d'autres valeurs (par exemple, l'extension de rendu Image utilise TIFF comme format de sortie par défaut ; vous pouvez modifier les paramètres d'extension et utiliser le format EMF à la place).  
  
 La modification des paramètres d'extension de rendu affecte uniquement les opérations de rendu sur le serveur de rapports. Vous ne pouvez pas remplacer les paramètres d'extension de rendu en mode d'aperçu de rapport dans le Concepteur de rapports.  
  
 La spécification des paramètres d'extension de rendu dans les fichiers de configuration a des répercussions globales sur les extensions de rendu. Les paramètres des fichiers de configuration sont utilisés à la place des valeurs par défaut chaque fois qu'une extension de rendu particulière est employée. Si vous souhaitez définir des paramètres d’extension de rendu pour une opération de rapport ou de rendu spécifique, vous devez spécifier par programmation les informations sur l’appareil à l’aide de la méthode <xref:ReportExecution2005.ReportExecutionService.Render%2A> ou en spécifiant les paramètres d’informations d’appareil sur une URL de rapport. Pour obtenir la liste complète des paramètres d’informations sur l’appareil et davantage d’informations sur la spécification de paramètres d’informations sur l’appareil pour une opération de rendu, consultez [Transmission de paramètres d’informations de périphérique aux extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="finding-and-modifying-rsreportserverconfig"></a>Recherche et modification de RSReportServer.config  
 Les paramètres de configuration des formats de sortie des rapports sont spécifiés sous forme de paramètres d'extension de rendu dans le fichier RSReportServer.config. Pour spécifier les paramètres d'extension de rendu dans les fichiers de configuration, vous devez savoir comment définir les structures XML qui configurent les paramètres de rendu. Vous pouvez modifier deux structures XML :  
  
-   Le `OverrideNames` élément définit le nom d’affichage et la langue de l’extension de rendu.  
  
-   Le `DeviceInfo` structure XML définit les paramètres d’informations de périphérique qui sont utilisés par une extension de rendu. La plupart des paramètres d'extension de rendu sont spécifiés en tant que paramètres d'informations de périphérique.  
  
 Vous pouvez utiliser un éditeur de texte pour modifier le fichier. Le fichier RSReportServer.config est situé dans le dossier \Reporting Services\Report Server\Bin. Pour plus d’informations sur la modification des fichiers de configuration, consultez [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## <a name="changing-the-display-name"></a>Modification du nom complet  
 Le nom complet d'une extension de rendu apparaît dans la liste Exporter de la barre d'outils Rapport. Un nom complet par défaut peut être, par exemple, au format archive Web, fichier TIFF et fichier Acrobat (PDF). Vous pouvez remplacer le nom d’affichage par défaut par une valeur personnalisée en spécifiant le `OverrideNames` élément dans les fichiers de configuration. De plus, si vous définissez deux instances d'une même extension de rendu, vous pouvez utiliser l'élément `OverrideNames` pour faire la distinction entre chaque instance dans la liste Exporter.  
  
 Étant donné que les noms complets sont localisés, vous devez définir le `Language` attribut si vous remplacez le nom d’affichage par défaut avec une valeur personnalisée. Dans le cas contraire, le nom que vous spécifiez sera ignoré. La valeur de langue que vous définissez doit être valide pour l'ordinateur serveur de rapports. Par exemple, si le serveur de rapports fonctionne sur un système d'exploitation français, vous devez indiquer « fr-FR » comme valeur d'attribut.  
  
 L'exemple suivant décrit comment fournir un nom personnalisé sur un serveur de rapports en anglais :  
  
```  
<Extension Name="XML" Type="Microsoft.ReportingServices.Rendering.DataRenderer.XmlDataReport,Microsoft.ReportingServices.DataRendering">  
   <OverrideNames>  
     <Name Language="en-US">My Custom Display Name for XML Rendering</Name>  
   </OverrideNames>  
</Extension>  
```  
  
## <a name="changing-device-information-settings"></a>Modification des paramètres d'informations de périphérique  
 Pour modifier les paramètres d'informations de périphérique par défaut qui sont utilisés par une extension de rendu déjà déployée sur votre serveur de rapports, vous devez taper la structure XML `DeviceInfo` dans les fichiers de configuration. Chaque extension de rendu prend en charge des paramètres d'informations de périphérique qui sont uniques pour cette extension. Pour afficher la liste complète des paramètres d’informations de périphérique, consultez [en passant des paramètres d’informations de périphérique aux Extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
 L'exemple suivant illustre la syntaxe et la structure XML qui modifie les paramètres par défaut de l'extension de rendu Image :  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">Image (EMF)</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <ColorDepth>32</ColorDepth>  
                <DpiX>300</DpiX>  
                <DpiY>300</DpiY>  
                <OutputFormat>EMF</OutputFormat>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="configuring-multiple-entries-for-a-rendering-extension"></a>Configuration de plusieurs entrées pour une extension de rendu  
 Vous pouvez créer plusieurs instances de la même extension de rendu pour prendre en charge différentes options de présentation. Chaque instance que vous définissez peut comporter sa propre combinaison de valeurs de paramètres. Lorsque vous définissez de nouvelles instances d'une expression de rendu existante, veillez à prendre en compte les points suivants :  
  
-   Spécifiez un nom unique pour l'extension.  
  
     Chaque instance doit avoir une valeur unique pour le `Name` attribut. L'exemple suivant utilise les noms « IMAGE (EMF Landscape) » et « IMAGE (EMF Portrait) » afin de faire la distinction entre les deux instances.  
  
     Soyez vigilent lorsque vous modifiez le nom d'une extension de rendu qui est déjà déployée. Les développeurs qui spécifient des extensions de rendu par programmation utilisent le nom de l'extension afin d'identifier l'instance à employer pour une opération de rendu particulière. Si vous exécutez des applications [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] personnalisées sur votre serveur de rapports, vérifiez que le développeur est informé quand vous modifiez une extension de rendu existante ou ajoutez une nouvelle extension.  
  
-   Spécifiez un nom complet unique afin que les utilisateurs puissent comprendre les différences de chaque format de sortie.  
  
     Si vous configurez plusieurs versions de la même extension, vous pouvez attribuer à chaque version un nom unique en fournissant une valeur pour `OverrideNames`. Si vous ne le faites pas, toutes les versions de l'extension sembleront porter le même nom dans la liste d'options Exporter de la barre d'outils.  
  
 L'exemple suivant illustre l'utilisation de l'extension de rendu Image par défaut (qui génère une sortie au format TIFF) vers une sortie EMF en mode Portrait avec une seconde instance qui génère des rapports au format EMF en mode Paysage. Notez que chaque nom d'extension est unique. Lorsque vous testez cet exemple, n'oubliez pas de choisir des rapports qui ne contiennent pas de fonctions interactives telles que les options d'affichage/masquage, des matrices ou des liens d'extraction (les fonctions interactives ne fonctionnent pas dans l'extension de rendu Image) :  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF Landscape)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Landscape Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>8.5in</PageHeight>  
                <PageWidth>11in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
    <Extension Name="IMAGE (EMF Portrait)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Portait Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>11in</PageHeight>  
                <PageWidth>8.5in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de Configuration RSReportServer](report-server/rsreportserver-config-configuration-file.md)   
 [Fichier de configuration RSReportDesigner](report-server/rsreportdesigner-configuration-file.md)   
 [Paramètres d’informations de périphérique CSV](csv-device-information-settings.md)   
 [Paramètres d’informations de périphérique Excel](excel-device-information-settings.md)   
 [Paramètres d’informations de périphérique HTML](html-device-information-settings.md)   
 [Paramètres d’informations de périphérique pour l’image](image-device-information-settings.md)   
 [Paramètres d’informations de périphérique pour le format de rendu MHTML](mhtml-device-information-settings.md)   
 [Paramètres d’informations de périphérique PDF](pdf-device-information-settings.md)   
 [Paramètres des informations de périphériques XML](xml-device-information-settings.md)  
  
  