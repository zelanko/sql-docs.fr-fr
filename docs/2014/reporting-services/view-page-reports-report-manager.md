---
title: Page vue, rapports (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4874ba29-429b-4dd4-a8cb-d4f087237dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8731c1d0f79d99919c4a087521565a6ec590278
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66098739"
---
# <a name="view-page-reports-report-manager"></a>Page Vue, Rapports (Gestionnaire de rapports)
  La page Afficher des rapports vous permet d'afficher un rapport. Lorsque vous ouvrez pour la première fois un rapport dans le Gestionnaire de rapports, il est au format HTML. Les rapports HTML incluent une barre d'outils Rapport qui s'affiche en haut du rapport et vous permet de parcourir les pages du rapport, d'effectuer une recherche dans un rapport et d'exporter le rapport dans un format différent. L'illustration suivante représente la barre d'outils Rapport :  
  
 ![Barre d’outils Rapport](media/htmlviewer-toolbar.gif "Barre d’outils Rapport")  
Barre d'outils Rapports  
  
 Dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], vous pouvez configurer les rapports de manière à ce qu'ils s'exécutent à la demande ou à partir d'un instantané d'exécution de rapport. Si un rapport est exécuté à la demande, le traitement des données et du rapport s'effectue à chaque ouverture. Si vous visualisez un rapport configuré de manière à ce qu'il s'exécute en tant qu'instantané d'exécution de rapport, le traitement des données s'est produit à la création de l'instantané.  
  
## <a name="exporting-reports"></a>Exportation des rapports  
 Toutes les fonctionnalités de rapport ne sont pas disponibles dans tous les formats d'exportation. Si vous exportez un rapport HTML vers un autre format, attendez-vous à voir certaines différences d'affichage du rapport. De plus, si le rapport inclut des fonctionnalités interactives (telles que les liens hypertexte, les signets et les explorateurs de documents), ces fonctionnalités peuvent ne pas être disponibles ou ne pas fonctionner de la même manière dans le nouveau format.  
  
## <a name="generating-data-feeds-from-report-data"></a>Génération de sources de données à partir de données de rapport  
 Vous pouvez générer des sources de données à partir de rapports. L'extension de rendu Atom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] génère deux documents conformes à Atom : un document de service Atom qui répertorie les flux de données fournis par le rapport et les flux de données qui contiennent les données du rapport. Les flux de données sont générés par [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dans un format standardisé conforme à Atom 1.0, qu'il est possible de lire et d'échanger avec les applications qui utilisent des flux de données conformes à Atom. Par exemple, le client [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] peut utiliser des flux de données générés à partir de rapports.  
  
## <a name="running-parameterized-reports"></a>Exécuter des rapports paramétrables  
 Un rapport qui contient des champs d'entrée et un bouton **Afficher le rapport** est un rapport paramétrable. Pour afficher un rapport paramétrable, il est possible que vous deviez fournir des valeurs utilisées pour exécuter le rapport.  
  
> [!NOTE]  
>  Les instantanés d'exécution de rapport et certains formats d'exportation ne sont pas disponibles dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour plus d'informations, consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
