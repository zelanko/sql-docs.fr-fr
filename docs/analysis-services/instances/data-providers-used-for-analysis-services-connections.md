---
title: "Fournisseurs de données utilisés pour les connexions Analysis Services | Documents Microsoft"
ms.custom: 
ms.date: 01/23/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 816919b48f77a4462e8d0f0f04d0bb621a2d2058
ms.sourcegitcommit: 3206a31870f8febab7d1718fa59fe0590d4d45db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Bibliothèques clientes (fournisseurs de données) utilisés pour les connexions Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services fournit trois bibliothèques clientes, également appelé **des fournisseurs de données**, pour le serveur et l’accès aux données depuis les outils et les applications clientes. Outils tels que des applications telles que Power BI Desktop et Excel se connectent à Analysis Services à l’aide de ces bibliothèques et SSDT et SSMS. Deux des bibliothèques clientes, ADOMD.NET et Analysis Services Management Objects (AMO) sont des bibliothèques de client géré. Le fournisseur OLE DB pour Analysis Services (MSOLAP DLL) est une bibliothèque cliente native. Les bibliothèques clientes sont les mêmes pour SQL Server Analysis Services et Azure Analysis Services.
  
##  <a name="bkmk_downloadsite"></a>Où obtenir des versions plus récentes  
 La version installée sur un ordinateur client doit correspondre à la version principale du serveur qui fournit les données. Si l'installation du serveur est plus récente que les fournisseurs de données installés sur les stations de travail de votre réseau, vous devrez peut-être installer les dernières bibliothèques disponibles.  

Bibliothèques clientes incluses dans les Packs de fonctionnalités SQL Server antérieures correspondent à cette version SQL. Toutefois, ils ne peuvent pas être plus tard. Connexion à Azure Analysis Services peut nécessiter des versions ultérieures. Toutes les versions sont à compatibilité descendante.

Pour obtenir la dernière version, consultez [les bibliothèques clientes pour la connexion à Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
