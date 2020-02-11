---
title: Afficher un aperçu des rapports
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 21928cd6637815000983e8a0fe05aa4e77d1c216
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67412973"
---
# <a name="preview-reports-in-sql-server-reporting-services-ssrs"></a>Afficher un aperçu des rapports dans SQL Server Reporting Services (SSRS)

  Lorsque vous concevez un rapport, vous pouvez le visualiser avant de le publier sur l'environnement de production. Pour ce faire, vous disposez de plusieurs méthodes : en passant en mode aperçu dans le Concepteur de rapports, en utilisant la fenêtre d'aperçu du Concepteur de rapports et en publiant le rapport sur un serveur de rapports dans un environnement de test.  
  
> [!NOTE]  
> Lorsque vous prévisualisez un rapport, les données de ce rapport sont mises en cache dans un fichier sur l'ordinateur local. Ainsi, lorsque vous prévisualisez une nouvelle fois ce rapport (au moyen des mêmes requête, paramètres et informations d'identification), le Concepteur de rapports récupère l'exemplaire mis en cache au lieu d'exécuter à nouveau la requête. Le fichier de données est enregistré * \< *sous le compte ReportName>. rdl. Data dans le même répertoire que le fichier de définition de rapport. Le fichier n'est pas supprimé lorsque vous fermez le Générateur de rapports.  
  
## <a name="preview-mode"></a>Mode Aperçu

 Vous pouvez afficher un aperçu d’un rapport dans Concepteur de rapports en cliquant sur **Aperçu**. Cette opération entraîne l'exécution du rapport localement. Elle utilise les mêmes fonctionnalités de traitement et de rendu de rapport que celles fournies par le serveur de rapports. Le rapport qui est affiché est une image interactive. Vous pouvez sélectionner des paramètres, cliquer sur des liens, afficher l'explorateur de documents, et développer ou réduire des zones masquées du rapport. Vous pouvez aussi exporter le rapport dans n'importe quel format de rendu installé.  
  
## <a name="standalone-preview"></a>Afficheur

 Une autre manière d'afficher l'aperçu d'un rapport consiste à exécuter le projet de rapport dans une configuration de débogage, par exemple pour déboguer les assemblys personnalisés que vous écrivez. Vous pouvez exécuter un projet de trois manières :  
  
- En cliquant sur **Démarrer** dans le menu **Déboguer** .  
  
- En cliquant sur le bouton **Démarrer** dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la barre d’outils standard.  
  
- En appuyant sur F5.  
  
 Si vous utilisez une configuration de projet qui crée le rapport mais ne le déploie pas, le rapport spécifié dans la propriété `StartItem` de la configuration actuelle s'ouvre dans une fenêtre d'aperçu distincte. La fenêtre d'aperçu affiche le rapport de la même manière et avec les mêmes fonctionnalités que le mode Aperçu.  
  
> [!NOTE]  
> Avant de déboguer un rapport, vous devez définir un élément de départ. Pour définir un élément de départ, dans Explorateur de solutions, cliquez avec le bouton droit sur le **** projet de rapport, cliquez `StartItem`sur Propriétés, puis dans, sélectionnez le nom du rapport à afficher.  
  
 Si vous souhaitez afficher l’aperçu d’un rapport particulier, sans qu’il soit l’élément de départ du projet, sélectionnez une configuration qui crée le rapport mais ne le déploie pas (par exemple, la configuration DebugLocal), cliquez avec le bouton droit sur le rapport, puis sélectionnez **Exécuter**. Vous devez choisir une configuration qui ne déploie pas le rapport, sinon il sera publié sur le serveur de rapports au lieu de s'afficher localement dans une fenêtre d'aperçu.  
  
## <a name="print-preview"></a>Aperçu avant impression

 Lorsque vous affichez pour la première fois un rapport en mode Aperçu ou dans la fenêtre d'aperçu, le rapport prévisualisé ressemble à un rapport créé par l'extension de rendu HTML. L'aperçu n'est pas en HTML, mais la présentation et la pagination du rapport sont similaires à un affichage HTML.  
  
 Vous pouvez changer la vue pour afficher le rapport tel qu'il sera imprimé en activant le mode d'aperçu avant impression. Cliquez sur le bouton **Aperçu avant impression** dans la barre d'outils d'aperçu. Le rapport s'affiche comme sur une véritable page. Ce que vous voyez ressemble au résultat que produisent les extensions de rendu Image et PDF. L'aperçu avant impression n'est pas une image ni un fichier PDF, mais la disposition et la pagination du rapport sont similaires à celles de ces formats.  
  
## <a name="publish-to-a-test-server"></a>Publier sur un serveur de test

 Vous pouvez également tester les rapports en les publiant sur un serveur de test. La publication d'un rapport sur un serveur de test revient, au niveau de la procédure, à publier un rapport sur un serveur de production. Pour plus d’informations sur la publication d’un rapport, consultez [Publication de rapports sur un serveur de rapports](publishing-reports-to-a-report-server.md).  
  
## <a name="next-steps"></a>Étapes suivantes

 - [Imprimer des rapports &#40;Générateur de rapports et SSRS&#41;](../report-builder/print-reports-report-builder-and-ssrs.md)
 - [Imprimer un rapport &#40;Générateur de rapports et SSRS&#41;](../report-builder/print-a-report-report-builder-and-ssrs.md)
 - [Publier des rapports](../publish-reports.md)
 - [Utilisation d'assemblages personnalisés avec des rapports](../custom-assemblies/using-custom-assemblies-with-reports.md)