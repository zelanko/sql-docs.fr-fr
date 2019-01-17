---
title: Cartes personnalisées dans les rapports mobiles Reporting Services | Microsoft Docs
description: Découvrez les cartes géographiques de l’Éditeur de rapports mobiles SQL Server, définies dans un format appelé « fichiers de forme ESRI ».
ms.date: 12/06/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 59a4ebad-587a-4770-afcd-c69216b8afd9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 17975defea6029e4077acbe45fd3f8b0d7495267
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53212078"
---
# <a name="custom-maps-in-reporting-services-mobile-reports"></a>Custom maps in Reporting Services mobile reports
Dans l’Éditeur de rapports mobiles SQL Server, les cartes géographiques sont définies dans un format appelé *fichiers de forme ESRI*.  
  
Ce format semi-ouvert étendu initialement conçu par une société privée est utilisé dans une grande partie des applications GIS. Pour se conformer à ce format, l’Éditeur de rapports mobiles requiert la fourniture de deux fichiers lors de la définition d’une carte :  
  
- Un fichier .SHP pour les géométries de forme  
- Un fichier .DBF pour les métadonnées  
  
Les noms des fichiers de base doivent correspondre (par ex., *canada.shp* et *canada.dbf*). Les métadonnées doivent inclure le champ *NAME* avec la valeur du nom de la forme correspondante (key), pour être utilisées lors de l’ajout des données dans la carte.  

La taille cumulée des deux fichiers de mappage (SHP et DBF) ne doit pas dépasser 512 Ko. Si les fichiers de mappage sont trop volumineux, vous pouvez réduire leur taille à l’aide d’un outil tel que [https://mapshaper.org/](https://mapshaper.org/).  
  
Découvrez comment [ajouter des mappages personnalisés aux rapports mobiles](../../reporting-services/mobile-reports/add-a-custom-map-to-a-reporting-services-mobile-report.md).  
  
## <a name="technical-information"></a>Informations techniques  
  
- La spécification officielle : [https://www.esri.com/library/whitepapers/pdfs/shapefile.pdf](https://www.esri.com/library/whitepapers/pdfs/shapefile.pdf)  
- L’article Wikipedia sur le fichier de forme : [https://en.wikipedia.org/wiki/Shapefile](https://en.wikipedia.org/wiki/Shapefile)  
  
## <a name="creating--editing-map-geometry"></a>Création et modification d’une géométrie de carte  
  
La création et la modification des fichiers de forme sont un processus complexe qui n’entre pas dans le cadre de ce document. Voici quelques ressources et applications qui vous aideront à démarrer :  
  
- ArcGIS : [https://www.arcgis.com/](https://www.arcgis.com/)  
- Plug-in MAPublisher pour Adobe Illustrator : [https://www.avenza.com/mapublisher](https://www.avenza.com/mapublisher)  
- QuantumGIS (gratuit) : [https://www.qgis.org/](https://www.qgis.org/)  

## <a name="existing-shapefiles"></a>Fichiers de forme existants  
  
Il est possible de télécharger plusieurs fichiers de forme existants à partir de sites web comme Diva-GIS : [https://www.diva-gis.org/Data](https://www.diva-gis.org/Data).  

## <a name="see-also"></a>Voir aussi  
- [Maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Créer et publier des rapports mobiles avec l’Éditeur de rapports mobiles SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
