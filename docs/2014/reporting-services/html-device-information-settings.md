---
title: Paramètres d’informations de périphérique HTML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- HTML [Reporting Services], rendering
- device information settings [Reporting Services], HTML rendering
ms.assetid: f505f478-dd6d-444a-957c-34f7cfb98911
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8e5f34ac12dd76de22e53be72e04d51d0cef8be1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63260851"
---
# <a name="html-device-information-settings"></a>Paramètres d'informations de périphérique HTML
  Le tableau suivant répertorie les paramètres d'informations de périphérique qui permettent un rendu du rapport au format HTML.  
  
> [!IMPORTANT]  
>  Les paramètres d’informations de périphérique répertoriés dans le tableau ci-dessous avec **(\*)** sont déconseillés et ne doivent pas être utilisés dans les nouvelles applications. Pour plus d’informations, consultez [déconseillées dans SQL Server Reporting Services dans SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md).  
  
|Paramètre|Value|  
|-------------|-----------|  
|`AccessibleTablix`|Indique s'il faut effectuer le rendu avec des métadonnées d'accessibilité supplémentaires en vue de l'utilisation d'un lecteur d'écran. Ce paramètre est uniquement applicable aux rapports qui contiennent une seule table ou une structure matricielle avec regroupement simple. La valeur par défaut est `false`. Les métadonnées d'accessibilité supplémentaires imposent la mise en conformité du rapport eu égard des normes techniques suivantes décrites dans la section « Intranet Web et Applications et Informations Internet » (1194.22) du document relatif aux normes d'accessibilité dans le domaine de l'électronique et des technologies de l'information (Section 508) :<br /><br /> (g) les en-têtes de ligne et de colonne doivent être identifiés pour les tables de données.<br /><br /> (h) le balisage doit être utilisé pour associer les cellules de données aux cellules d'en-tête pour les tables de données qui ont plusieurs niveaux logiques d'en-têtes de ligne ou de colonne.<br /><br /> (i) les cadres doivent porter un titre qui facilite l'identification du cadre et la navigation.<br /><br /> Ce paramètre est pris en charge dans [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[SPS2010](../includes/sps2010-md.md)], mais pas dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[SPS2007](../includes/sps2007-md.md)].|  
|**ActionScript(\*)**|Spécifie le nom de la fonction JavaScript à utiliser lorsqu'un événement d'action se produit, tel qu'une extraction ou un clic pour atteindre un signet. Si ce paramètre est spécifié, un événement d'action déclenchera la fonction JavaScript nommée au lieu d'une publication sur le serveur.|  
|**BookmarkID**|Identificateur du signet à atteindre dans le rapport.|  
|**DocMap**|Indique s'il faut afficher ou masquer l'Explorateur de documents du rapport. La valeur par défaut de ce paramètre est `true`.|  
|`ExpandContent`|Indique si le rapport doit être placé dans une structure de table qui restreint la taille horizontale.|  
|**FindString**|Texte à rechercher dans le rapport. La valeur par défaut de cette propriété est une chaîne vide.|  
|**GetImage (\*)**|Obtient une icône particulière pour l'interface utilisateur de la visionneuse HTML.|  
|`HTMLFragment`|Indique si un fragment HTML est créé à la place d'un document HTML complet. Les fragments HTML font figurer le contenu du rapport dans un élément TABLE et omettent les éléments HTML et BODY. La valeur par défaut est `false`. Le rendu à l'aide de SOAP avec la propriété `HTMLFragment` définie sur `true` crée des URL contenant des informations de session qui peuvent être utilisées pour demander correctement les images. Les images doivent être des ressources téléchargées dans la base de données du serveur de rapports.|  
|`ImageConsolidation`|Indique s'il faut consolider le rendu du graphique, du plan, de la jauge ou des images d'indicateurs en une grande image. La consolidation d'aides visuelles améliore la performance du rapport dans le navigateur client lorsque le rapport contient un grand nombre d'éléments de visualisation des données. La valeur par défaut est `true` pour les navigateurs les plus récents.|  
|**JavaScript**|Indique si JavaScript est pris en charge dans le rapport rendu. La valeur par défaut est `true`.|  
|`LinkTarget`|Cible des liens hypertexte contenus dans le rapport. Vous pouvez cibler une fenêtre ou frame en fournissant le nom de la fenêtre, tel que `LinkTarget` = *window_name*, ou vous pouvez cibler une nouvelle fenêtre en utilisant `LinkTarget`= _blank. D'autres noms de cibles valides incluent _self, _parent et _top.|  
|**OnlyVisibleStyles(\*)**|Indique que seuls les styles partagés pour la page actuellement rendue sont générés.|  
|`OutlookCompat`|Indique s'il convient d'effectuer le rendu avec des métadonnées supplémentaires qui font que l'aspect du rapport est meilleur dans Outlook. Pour d'autres, la valeur par défaut est `false`.|  
|**Paramètres**|Indique s'il faut afficher ou masquer la zone des paramètres de la barre d'outils. Si vous affectez à ce paramètre la valeur `true`, la zone des paramètres de la barre d'outils s'affiche. La valeur par défaut de ce paramètre est `true`.|  
|`PrefixId`|Lorsque ce paramètre est utilisé avec `HTMLFragment`, ajoute le préfixe spécifié à tous les attributs `ID` dans le fragment HTML qui est créé.|  
|**ReplacementRoot(\*)**|Chaîne à ajouter à tous les liens d'extraction, de bascule et de signet dans le rapport lors du rendu hors du contrôle ReportViewer. Par exemple, ce paramètre est utilisé pour rediriger le clic d’un utilisateur vers une page personnalisée.|  
|**ResourceStreamRoot(\*)**|Chaîne à ajouter à l'URL pour toutes les ressources d'image, telles que les images bascule ou de tri.|  
|**Section**|Numéro de page du rapport dont le rendu est effectué. La valeur `0` indique que toutes les sections du rapport sont rendues. La valeur par défaut est `1`.|  
|**StreamRoot (\*)**|Chemin d'accès utilisé pour préfixer la valeur de l'attribut **src** de l'élément IMG dans le rapport HTML retourné par le serveur de rapports. Par défaut, le serveur de rapports fournit le chemin d'accès. Vous pouvez utiliser ce paramètre pour spécifier un chemin racine pour les images contenues dans un rapport (par exemple, **http://\<nom_serveur>/resources/companyimages**).|  
|**StyleStream**|Indique si les styles et les scripts sont créés en tant que flux distinct plutôt que dans le document. La valeur par défaut est `false`.|  
|`Toolbar`|Indique s'il faut afficher ou masquer la barre d'outils. La valeur par défaut de ce paramètre est `true`. Si la valeur de ce paramètre est `false`, toutes les options restantes (sauf le plan du document) sont ignorées. Si vous omettez ce paramètre, la barre d'outils s'affiche automatiquement pour les formats de rendu assurant sa prise en charge.<br /><br /> Le rendu de la barre d'outils de la Visionneuse de rapports est effectué lorsque vous utilisez l'accès URL pour effectuer le rendu d'un rapport. Le rendu de la barre d'outils ne s'effectue pas via l'API SOAP. Toutefois, le paramètre d'informations de périphérique `Toolbar` affecte la façon dont le rapport s'affiche lors de l'utilisation de la méthode SOAP `Render`. Si la valeur de ce paramètre est `true` lorsque vous utilisez SOAP pour effectuer un rendu au format HTML, seule la première section du rapport est rendue. Si la valeur est `false`, le rendu du rapport HTML entier est effectué sous la forme d'une page HTML unique.|  
|`UserAgent`|Chaîne `user-agent` du navigateur qui effectue la demande, qui figure dans la requête HTTP.|  
|**Zoom (\*)**|Valeur du zoom du rapport sous forme de pourcentage entier ou de constante de chaîne. Les valeurs de chaîne standard incluent les valeurs `Page Width` et `Whole Page`. Ce paramètre est ignoré par les versions de [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer antérieures à la version 5.0 et par tous les navigateurs non-[!INCLUDE[msCoName](../includes/msconame-md.md)] . La valeur par défaut de ce paramètre est `100`.|  
|**DataVisualizationFitSizing**|Indique le comportement d'ajustement de la visualisation des données à l'intérieur d'un tableau matriciel. Cela inclut le graphique, la jauge et la carte.<br /><br /> Les valeurs possibles sont **Approximatif** et **Exact**.<br /><br /> La valeur par défaut est **Approximatif**. Si le paramètre est supprimé du fichier **rsreportserver.config** , le comportement par défaut est **Exact**.<br /><br /> L’activation de l’option **Exact** peut avoir un impact sur les performances, car le traitement permettant de déterminer la taille peut prendre plus de temps.|  
  
## <a name="see-also"></a>Voir aussi  
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
