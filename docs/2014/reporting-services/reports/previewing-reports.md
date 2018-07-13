---
title: Aperçu des rapports | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], previewing reports
- previewing reports [Reporting Services]
- printing previews
- test servers [Reporting Services]
ms.assetid: 85117f6c-828e-45c9-810f-e700d9bfba67
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: afcfb2cf31526f4e8898fafbe72f9492a1848886
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202529"
---
# <a name="previewing-reports"></a>Aperçu des rapports
  Lorsque vous concevez un rapport, vous pouvez le visualiser avant de le publier sur l'environnement de production. Pour ce faire, vous disposez de plusieurs méthodes : en passant en mode aperçu dans le Concepteur de rapports, en utilisant la fenêtre d'aperçu du Concepteur de rapports et en publiant le rapport sur un serveur de rapports dans un environnement de test.  
  
> [!NOTE]  
>  Lorsque vous prévisualisez un rapport, les données de ce rapport sont mises en cache dans un fichier sur l'ordinateur local. Ainsi, lorsque vous prévisualisez une nouvelle fois ce rapport (au moyen des mêmes requête, paramètres et informations d'identification), le Concepteur de rapports récupère l'exemplaire mis en cache au lieu d'exécuter à nouveau la requête. Le fichier de données est enregistré sous *\<nom_rapport>*.rdl.data dans le même répertoire que le fichier de définition de rapport. Le fichier n'est pas supprimé lorsque vous fermez le Générateur de rapports.  
  
## <a name="preview-mode"></a>Mode Aperçu  
 Vous pouvez prévisualiser un rapport dans le Concepteur de rapports en cliquant sur **aperçu**. Cette opération entraîne l'exécution du rapport localement. Elle utilise les mêmes fonctionnalités de traitement et de rendu de rapport que celles fournies par le serveur de rapports. Le rapport qui est affiché est une image interactive. Vous pouvez sélectionner des paramètres, cliquer sur des liens, afficher l'explorateur de documents, et développer ou réduire des zones masquées du rapport. Vous pouvez aussi exporter le rapport dans n'importe quel format de rendu installé.  
  
## <a name="standalone-preview"></a>Afficheur  
 Une autre manière d'afficher l'aperçu d'un rapport consiste à exécuter le projet de rapport dans une configuration de débogage, par exemple pour déboguer les assemblys personnalisés que vous écrivez. Vous pouvez exécuter un projet de trois manières :  
  
-   En cliquant sur **Démarrer** sur le **déboguer** menu.  
  
-   En cliquant sur le **Démarrer** bouton sur le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] barre d’outils standard.  
  
-   En appuyant sur F5.  
  
 Si vous utilisez une configuration de projet qui crée le rapport mais ne le déploie pas, le rapport est spécifié dans le `StartItem` propriété de la configuration actuelle s’ouvre dans une fenêtre d’aperçu distincte. La fenêtre d'aperçu affiche le rapport de la même manière et avec les mêmes fonctionnalités que le mode Aperçu.  
  
> [!NOTE]  
>  Avant de déboguer un rapport, vous devez définir un élément de départ. Pour définir un élément de départ, dans l’Explorateur de solutions, cliquez sur le projet de rapport, cliquez sur **propriétés**, puis dans `StartItem`, sélectionnez le nom du rapport à afficher.  
  
 Si vous souhaitez afficher l’aperçu d’un rapport particulier, sans qu’il soit l’élément de départ du projet, sélectionnez une configuration qui crée le rapport mais ne le déploie pas (par exemple, la configuration DebugLocal), cliquez avec le bouton droit sur le rapport, puis sélectionnez **Exécuter**. Vous devez choisir une configuration qui ne déploie pas le rapport, sinon il sera publié sur le serveur de rapports au lieu de s'afficher localement dans une fenêtre d'aperçu.  
  
## <a name="print-preview"></a>Aperçu avant impression  
 Lorsque vous affichez pour la première fois un rapport en mode Aperçu ou dans la fenêtre d'aperçu, le rapport prévisualisé ressemble à un rapport créé par l'extension de rendu HTML. L'aperçu n'est pas en HTML, mais la présentation et la pagination du rapport sont similaires à un affichage HTML.  
  
 Vous pouvez changer la vue pour afficher le rapport tel qu'il sera imprimé en activant le mode d'aperçu avant impression. Cliquez sur le bouton **Aperçu avant impression** dans la barre d'outils d'aperçu. Le rapport s'affiche comme sur une véritable page. Ce que vous voyez ressemble au résultat que produisent les extensions de rendu Image et PDF. L'aperçu avant impression n'est pas une image ni un fichier PDF, mais la disposition et la pagination du rapport sont similaires à celles de ces formats.  
  
## <a name="publishing-to-a-test-server"></a>Publication sur un serveur de test  
 Vous pouvez également tester les rapports en les publiant sur un serveur de test. La publication d'un rapport sur un serveur de test revient, au niveau de la procédure, à publier un rapport sur un serveur de production. Pour plus d’informations sur la publication d’un rapport, consultez [Publication de rapports sur un serveur de rapports](publishing-reports-to-a-report-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Imprimer des rapports &#40;Générateur de rapports et SSRS&#41;](../report-builder/print-reports-report-builder-and-ssrs.md)   
 [Imprimer un rapport &#40;Générateur de rapports et SSRS&#41;](../report-builder/print-a-report-report-builder-and-ssrs.md)   
 [Publier des rapports](../publish-reports.md)   
 [Utilisation d'assemblages personnalisés avec des rapports](../custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
