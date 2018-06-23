---
title: Modifier une source de partition pour utiliser une table de faits différentes | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fact tables [Analysis Services]
- partitions [Analysis Services], fact tables
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7355f5f7430a5e74cd06ffa73c1b6ed68e11a7c0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154285"
---
# <a name="change-a-partition-source-to-use-a-different-fact-table"></a>Modifier une source de partition afin d'utiliser une table de faits différente
  Lorsque vous créez une partition pour un cube, vous pouvez décider d'utiliser une table de faits différente. Les tables différentes peuvent provenir d'une vue de source de données unique, de différentes vues de sources de données ou de différentes sources de données. Une vue de source de données peut également contenir des tables différentes provenant de plusieurs sources de données.  
  
 Toutes les tables de faits et dimensions des partitions d'un cube doivent avoir la même structure que la table de faits et les dimensions du cube. Par exemple, des tables de faits différentes peuvent avoir la même structure mais contenir des données pour différentes années ou différentes lignes de produits.  
  
 Vous spécifiez une table de faits dans la page **Spécifier des informations sur la source** de l’Assistant Partition. Dans cette page, dans le groupe Source de partition à côté de **Regarder dans**, spécifiez la source de données ou la vue de source de données à consulter. Ensuite, cliquez sur **Rechercher des tables**puis, sous **Tables disponibles**, sélectionnez la table à utiliser.  
  
 Lorsque vous utilisez des tables de faits différentes, assurez-vous qu'aucune donnée n'est dupliquée dans les partitions. Par exemple, si une table de faits contient uniquement les transactions de l'année 2012 et qu'une autre table de faits contient uniquement les transactions de l'année 2013, ces tables contiennent des données distinctes. De même, les tables de faits réservées à des lignes de produits ou à des régions géographiques distinctes sont totalement indépendantes.  
  
 Il est possible, mais non conseillé, d'utiliser des tables de faits différentes contenant des données en double. Dans ce cas, vous devez utiliser des filtres dans les partitions pour vous assurer que les données utilisées par une partition ne sont pas utilisées aussi par une autre partition. Pour plus d’informations, consultez [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et gérer une Partition locale &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)  
  
  