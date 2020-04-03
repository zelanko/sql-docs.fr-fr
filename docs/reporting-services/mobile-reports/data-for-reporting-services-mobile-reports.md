---
title: Données pour les rapports mobiles Reporting Services | Microsoft Docs
description: Une fois que vous avez importé des données dans l’éditeur de rapports mobiles SQL Server, la création et la conception de rapports mobiles sont identiques, que les données proviennent de fichiers Excel ou de jeux de données partagés.
ms.date: 02/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3c022631d0f21c4e23756e39e4824fe9f52ef3b5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79447861"
---
# <a name="data-for-reporting-services-mobile-reports"></a>Data for Reporting Services mobile reports
Le modèle de données [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] est simple. Les données sont importées dans [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] comme une collection de datasets. Des relations formelles entre les datasets ne sont pas nécessaires. Les recherches entre deux datasets fonctionnent tant que les valeurs de clé correspondent. Les agrégations de date/heure sont traitées par le composant d’exécution de rapport mobile. Elles correspondent entre différents datasets, même si la granularité des données d’horodatage varie selon les datasets.   
  
Vous pouvez importer les données de deux types de sources :   
  
* **Fichiers Excel locaux** : sélectionnez un document Excel, puis la ou les feuilles de calcul à importer. Après l’importation, les données sont stockées dans la définition du rapport mobile. Pour actualiser les données provenant du fichier Excel d’origine, utilisez la commande **Actualiser les données** dans le coin supérieur droit de l’onglet [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] **Données**. En savoir plus sur la [préparation des données Excel pour les rapports mobiles SSRS](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md).  
  
* **Jeux de données partagés de l’Éditeur de rapports mobiles SQL Server** : parcourez la liste des jeux de données publiés sur le serveur et sélectionnez ceux à ajouter au rapport mobile. Les rapports mobiles basés sur les données du serveur restent toujours connectés aux jeux de données du serveur d’origine et reflètent l’état des données sur le serveur. Consultez la [liste des sources de données prises en charge](../report-data/data-sources-supported-by-reporting-services-ssrs.md).   
  
  Pour plus d’informations, consultez [Obtenir des données à partir de datasets partagés dans l’Éditeur de rapports mobiles](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md).  
  
Après avoir importé des données dans [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)], la procédure de conception et de création de rapports mobiles est la même, quelle que soit la provenance des données.   
  
## <a name="connect-mobile-report-elements-to-data"></a>Connecter des éléments de rapport mobile aux données ##  
  
Chaque élément de l’Éditeur de rapports mobiles SQL Server contient un ou plusieurs paramètres de données. Par exemple, l’élément Jauge radiale contient deux paramètres de données : Valeur principale et Valeur de comparaison. Chacun de ces paramètres pointe vers un champ (colonne) d’un dataset spécifique.   
  
Le composant d’exécution du rapport mobile fournit les valeurs agrégées de la jauge, selon les sélections de l’utilisateur. Notez que la valeur de comparaison de la même instance Jauge radiale peut être liée à un champ d’un autre dataset.   
  
### <a name="see-also"></a>Voir aussi  
-  [Préparer des données pour des rapports mobiles Reporting Services](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [Créer et publier des rapports mobiles avec l’Éditeur de rapports mobiles SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [Obtenir des données de jeux de données partagés](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [Conserver la mise en forme des dates pour Analysis Services dans les rapports mobiles](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  

