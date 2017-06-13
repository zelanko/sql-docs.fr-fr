---
title: "Utiliser des données simulées dans les rapports Reporting Services mobiles | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6baabc36-58fb-4a98-bb9c-c42bafb16d0f
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0eb83717100f70933d2b1fe00bcd19a8a2901f65
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="work-with-simulated-data-in-reporting-services-mobile-reports"></a>Utiliser des données simulées dans les rapports mobiles Reporting Services
Lorsque vous placez un élément de la galerie sur l’aire de conception, [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] génère immédiatement des données simulées pour cet élément. Lors de la création de rapports mobiles, ces données ont différentes utilités.   
  
![SS_MRP_SimDataTreeMapProps](../../reporting-services/mobile-reports/media/ss-mrp-simdatatreemapprops.png)  
  
Les données simulées sont utiles dans le cadre d’une approche de la création de rapports mobiles basée sur la conception. Si vous remplissez initialement les éléments avec des données simulées, vous pouvez créer rapidement des prototypes de rapports mobiles sans avoir à tenir compte des conditions spécifiques relatives aux données. Ces rapports mobiles peuvent ensuite servir à évaluer l’esthétique et l’efficacité globales.  
  
## <a name="create-an-excel-file-with-simulated-data-as-a-template"></a>Créer un fichier Excel avec des données simulées en tant que modèle  
  
Les données simulées fournissent également un modèle qui représente précisément les conditions relatives aux données d’une conception particulière de rapports mobiles.   
  
-  Cliquez sur **Exporter toutes les données** dans le coin supérieur droit de la vue de données.   
  
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] génère un document Excel contenant les données simulées (permettant de remplacer rapidement les données réelles) prêtes à être importées.   
  
## <a name="how-simulated-data-behaves"></a>Comportement des données simulées  
  
Les données simulées générées sont spécialement adaptées au rapport mobile que vous créez. Plus vous placez d’éléments sur l’aire de conception, plus les données simulées associées croissent et changent pour présenter le meilleur aperçu possible des données réelles. Cette évolution garantit que des options de filtres et de champs supplémentaires sont disponibles si vous ajoutez des séries supplémentaires aux visualisations de graphiques ou étendez la portée d’un ou plusieurs éléments de rapport mobile d’une autre façon.  
  
Comme mentionné précédemment, vous pouvez exporter des données simulées vers un fichier Excel, en créant un modèle de données convenant au rapport mobile associé. Vous pouvez insérer vos données réelles dans le fichier Excel et les réimporter dans l’ [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)].   
  
Une fois tous les contrôles liés aux données réelles, les tables simulées qui ne sont plus utilisées sont automatiquement supprimées du rapport mobile. Vous ne pouvez pas supprimer des tables simulées qui sont toujours référencées par des éléments sur l’aire de conception.  
  
>**Remarque**: Les données simulées n’augmentent pas l’encombrement global du rapport mobile parce qu’elles ne sont pas sérialisées avec le rapport mobile, mais générées à la volée pendant l’exécution.  
  
### <a name="see-also"></a>Voir aussi  
- [Créer et publier des rapports mobiles avec l’Éditeur de rapports mobiles SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  Affichez les [rapports mobiles SQL Server et les indicateurs de performance clés dans l’application iPad](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI pour iOS)  
-  Affichez les [rapports mobiles SQL Server et les indicateurs de performance clés dans l’application iPhone](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI pour iOS)  
  
  
  
  
  


