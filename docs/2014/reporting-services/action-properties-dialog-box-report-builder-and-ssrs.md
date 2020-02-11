---
title: Boîte de dialogue Propriétés de l’action (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.action.f1
- "10413"
- "10504"
- sql12.rtp.rptdesigner.calculatedseriesproperties.action.f1
- sql12.rtp.rptdesigner.pictureproperties.action.f1
- sql12.rtp.rptdesigner.actionproperties.f1
- sql12.rtp.rptdesigner.charttitleproperties.action.f1
- "10133"
- "10052"
- "10147"
- sql12.rtp.rptdesigner.chartproperties.action.f1
- "10122"
- sql12.rtp.rptdesigner.serieslabelproperties.action.f1
- sql12.rtp.rptdesigner.textboxproperties.action.f1
- "10162"
- "10168"
- sql12.rtp.rptdesigner.textproperties.action.f1
- sql12.rtp.rptdesigner.placeholderproperties.action.f1
- "10250"
- "10129"
- "10244"
- sql12.rtp.rptdesigner.seriesproperties.action.f1
ms.assetid: 2c5d915b-4f97-42cf-b8f1-49ca3ff3d0f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3d6069d5720121b02c627528ec772cb61ddb0a10
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66110080"
---
# <a name="action-properties-dialog-box-report-builder-and-ssrs"></a>Boîte de dialogue Propriétés relatives aux actions (Générateur de rapports et SSRS)
  Vous pouvez utiliser la boîte de dialogue **Action** pour activer les options de lien hypertexte pour un graphique, une jauge ou des éléments cartographiques prenant les liens en charge. Définissez une action afin qu'un utilisateur puisse cliquer sur le rapport et aller à une URL, à un rapport différent sur le même serveur de rapports ou sur un site SharePoint intégré à un serveur de rapports, ou encore à un emplacement différent dans le même rapport.  
  
## <a name="options"></a>Options  
 **Activer en tant qu'action**  
 Sélectionnez une option pour indiquer l'action à effectuer lorsque l'utilisateur clique sur l'élément.  
  
 **Aucun**  
 Choisissez cette option pour indiquer qu'aucune action n'est associée à l'élément.  
  
 **Atteindre le rapport**  
 Choisissez cette option pour créer un lien vers un rapport d'extraction situé sur un serveur de rapports. Les options supplémentaires suivantes s’affichent quand vous sélectionnez **Atteindre le rapport**.  
  
 **Spécifier un rapport**  
 Tapez ou sélectionnez le nom du rapport à utiliser en tant que rapport d'extraction. Les rapports d'extraction doivent se trouver sur le même serveur de rapports que ce rapport.  
  
 Pour un rapport publié sur un serveur de rapports configuré pour le mode natif, utilisez un chemin d'accès complet ou relatif sans l'extension de nom de fichier. Si le rapport se trouve dans le même dossier que le rapport actuel, utilisez uniquement le nom du rapport. Si le rapport se trouve dans un dossier différent sur le même serveur de rapports, utilisez un chemin d'accès relatif ou un chemin d'accès complet. Un chemin d'accès relatif commence à partir du dossier actif et remonte dans l'arborescence des dossiers, par exemple ../Dossier2/Rapport1. Un chemin d'accès complet démarre à partir de /, le dossier de base. Par exemple, /Rapports/Rapport1.  
  
 Pour un rapport publié sur un serveur de rapports configuré en mode intégré SharePoint, utilisez une URL complète incluant l'extension de nom de fichier (.rdl). Par exemple, http://*\<SharePointservername>/\<site>*/documents/rapport1.rdl. Les chemins d'accès relatifs ne sont pas pris en charge.  
  
 Pour plus d’informations, consultez [Spécification de chemins d’accès à des éléments externes &#40;Générateur de rapports et SSRS&#41;](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md) dans la [documentation du Générateur de rapports](https://go.microsoft.com/fwlink/?LinkId=154494) sur msdn.microsoft.com.  
  
 **Utilisez ces paramètres pour exécuter le rapport**  
 Ajoutez une liste de paramètres à transmettre au rapport d'extraction. Les noms des paramètres doivent correspondre aux paramètres définis pour le rapport cible. Utilisez les boutons **Ajouter** et **Supprimer** pour ajouter et supprimer des paramètres. Utilisez les flèches de direction pour ordonner la liste de paramètres.  
  
 **Ajouter**  
 Ajoutez un nouveau paramètre à transmettre au rapport d'extraction.  
  
 **Supprimer**  
 Supprimez un paramètre pour le rapport d'extraction.  
  
 **Flèche haut**  
 Déplacez le paramètre vers le haut de la liste.  
  
 **Flèche bas**  
 Déplacez le paramètre vers le bas de la liste.  
  
 **Nom**  
 Tapez le texte qui correspond au nom d'un paramètre défini dans le rapport d'extraction.  
  
 **Valeur**  
 Tapez ou sélectionnez une valeur à transmettre pour le paramètre nommé dans le rapport d'extraction. Cliquez sur le bouton **expression** (*FX*) pour modifier l’expression.  
  
 **Omettre**  
 Sélectionnez pour empêcher le paramètre de s'exécuter. Par défaut, cette case à cocher est désactivée et n'est pas active. Pour activer la case à cocher, cliquez sur le bouton **expression** (*FX*) et tapez **true** ou créez une expression. La case à cocher est activée lorsque vous cliquez sur **OK** dans la boîte de dialogue **expression** .  
  
 **Atteindre le signet**  
 Choisissez cette option pour définir un lien vers un signet dans le rapport actuel. L’option supplémentaire suivante s’affiche quand vous sélectionnez **Atteindre le signet**.  
  
 **Sélectionner un signet**  
 Tapez ou sélectionnez l'identificateur de signet du rapport à atteindre lorsque l'utilisateur clique sur le lien. Cliquez sur le bouton Expression (**FX**) pour modifier l’expression. L'identificateur du signet peut correspondre à un ID statique ou une expression ayant pour résultat un identificateur du signet. L'expression peut inclure un champ qui contient un identificateur de signet.  
  
 Pour définir un lien vers un signet, vous devez d'abord définir la propriété de signet d'un élément de rapport. Pour définir la propriété de signet, sélectionnez un élément de rapport et, dans le volet Propriétés, tapez une valeur ou expression pour l'identificateur du signet, par exemple, SalesChart ou 5TopSales.  
  
 **Atteindre l'URL**  
 Choisissez cette option pour définir un lien vers une page Web. Tapez ou sélectionnez l'URL d'une page Web, ou une expression qui prend la valeur de l'URL d'une page Web. Cliquez sur le bouton **expression** (*FX*) pour modifier l’expression. Cette expression peut inclure un champ qui contient une URL. L’option supplémentaire suivante s’affiche quand vous sélectionnez **Atteindre l’URL**.  
  
 **Sélectionner une URL**  
 Tapez ou entrez l'URL de l'élément. Pour un élément publié sur un serveur de rapports configuré pour le mode natif, utilisez un chemin d'accès complet ou relatif. Par exemple, http://*\<ServerName>*/images/image1.jpg. Pour un élément publié sur un serveur de rapports configuré en mode intégré SharePoint, utilisez une URL complète (par exemple, http://*\<SharePointservername>/\<site>*/documents/images/image1.jpg).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](report-design/charts-report-builder-and-ssrs.md)   
 [Aide Générateur de rapports pour les boîtes de dialogue, les volets et les assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [Ajouter un sous-rapport et des paramètres &#40;Générateur de rapports et SSRS&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md)   
 [Tri interactif, Explorateurs de documents et liens &#40;Générateur de rapports et SSRS&#41;](report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
  
