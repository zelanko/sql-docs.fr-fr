---
title: Ouvrir un rapport mobile avec des paramètres spécifiques de chaîne de requête | Microsoft Docs
ms.date: 10/25/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 4eeb3204-e207-4ac0-aff3-bfc4926e5754
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ca74d2d606dfddf394b0c7a32e8fe7d50f210934
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56296021"
---
# <a name="open-a-mobile-report-with-specific-query-string-parameters--reporting-services"></a>Ouvrir un rapport mobile avec des paramètres spécifiques de chaîne de requête | Reporting Services
Si vous avez un rapport mobile [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] avec des paramètres et une source de données [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)], vous pouvez inclure des paramètres de chaîne de requête dans l’URL du rapport afin qu’il s’ouvre automatiquement avec les valeurs que vous avez spécifiées. 
1.  Créez un [rapport mobiles avec des paramètres](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md).

2. Ouvrez le rapport dans l’Éditeur de rapports mobiles et sélectionnez l’onglet Données. 

2. Recherchez le nom de l’ensemble de données sur l’onglet dans la partie inférieure du tableau, et le nom de champ souhaité. 
    
    ![mobile-report-publisher-parameter-data-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-data-view.png)
    
2.  La syntaxe de l’URL dépend de votre source de données. 

     **Pour une source de données SQL Server Analysis Services** : Générez une URL avec un paramètre de chaîne de requête dans ce format :

    `https://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.<field-name>=<parameter-value>`

    Exemple :
    
    `https://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.category=Clothing` 
    
     **Pour une source de données SQL Server** : le paramètre de chaîne de requête est presque identique, sauf qu’il comporte le symbole \@ devant le nom de champ :

    `https://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.@<field-name>=<parameter-value>`

    Exemple :
    
      `https://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.@category=Clothing` 

    
3.  Cette URL ouvre le rapport sur le serveur, automatiquement filtrée sur la valeur de paramètre spécifiée.

    ![mobile-report-publisher-parameter-web-portal-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-web-portal-view.png)

### <a name="see-also"></a>Voir aussi

[Ajouter des paramètres à un rapport mobile](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)

