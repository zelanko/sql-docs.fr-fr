---
title: Ajouter une carte personnalisée à un rapport mobile Reporting Services | Microsoft Docs
ms.date: 01/31/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: fd259b95-bb58-4eb1-a436-6aa12fc6f5f2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9410aac6b74fbb515010517a2fe0667f3c197802
ms.sourcegitcommit: 1b0906979db5a276b222f86ea6fdbe638e6c9719
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971405"
---
# <a name="add-a-custom-map-to-a-reporting-services-mobile-report"></a>Ajouter une carte personnalisée à un rapport mobile Reporting Services
Les cartes personnalisées requièrent deux fichiers :  
* Un fichier SHP pour les géométries de forme  
* Un fichier DBF pour les métadonnées  
  
En savoir plus sur les [cartes personnalisées dans les rapports pour mobiles Reporting Services](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md).  
  
Stockez ces deux fichiers dans le même dossier. Les noms de ces deux fichiers doivent correspondre (par exemple, canada.shp et canada.dbf). La première colonne des métadonnées (fichier DBF) est utilisée pour établir une correspondance avec la valeur de clé du nom (clé) de la forme correspondante à utiliser lors du remplissage de la carte avec les données.
  
## <a name="load-a-custom-map"></a>Charger une carte personnalisée  
  
1. Sous l’onglet **Disposition**, sélectionnez un type de carte (**Carte thermique à gradient**, **Carte thermique à seuils** ou **Carte à bulles**), faites-la glisser sur l’aire de conception et donnez-lui la taille souhaitée.  
  
   ![SSMRP_MapsGallery](../../reporting-services/mobile-reports/media/ssmrp-mapsgallery.png)  
  
2. Dans la vue **Disposition** > panneau **Propriétés visuelles** > **Carte**, sélectionnez **Carte personnalisée d’un fichier**.   
  
   ![SSMRP_SelectCustomMap](../../reporting-services/mobile-reports/media/ssmrp-selectcustommap.png)  
  
3. Dans la boîte de dialogue **Ouvrir** , accédez à l’emplacement des fichiers SHP et DBF et sélectionnez les deux.   
  
   ![SSMRP_SelectDBFandSHP](../../reporting-services/mobile-reports/media/ssmrp-selectdbfandshp.png)  
  
## <a name="connect-data-to-a-custom-map"></a>Connecter des données à une carte personnalisée  
Lorsque vous ajoutez la carte personnalisée dans votre rapport, [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] la remplit avec des données géographiques simulées.  
  
![SSMRP_MapsData](../../reporting-services/mobile-reports/media/ssmrp-mapsdata.png)  
  
L’affichage des données réelles dans votre carte personnalisée est identique à celui des données dans les cartes intégrées. Suivez la procédure décrite dans [Cartes dans les rapports pour mobiles Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md) pour afficher vos données.  
  
### <a name="see-also"></a>Voir aussi  
- [Custom maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Cartes dans les rapports pour mobiles Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Créer et publier des rapports mobiles avec l’Éditeur de rapports mobiles SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
  
