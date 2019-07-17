---
title: Fournisseurs de données utilisés pour les connexions Analysis Services | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f5ba97f90b877896d68cd62598f11d0845fb698e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209533"
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Bibliothèques clientes (fournisseurs de données) utilisés pour les connexions Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services fournit trois bibliothèques clientes, également appelé **fournisseurs de données**, pour le serveur et l’accès aux données à partir des outils et les applications clientes. Outils tels que SSMS et SSDT et les applications telles que Power BI Desktop et Excel se connectent à Analysis Services à l’aide de ces bibliothèques. Deux des bibliothèques clientes, ADOMD.NET et Analysis Services Management Objects (AMO) sont des bibliothèques clientes managées. Le fournisseur OLE DB pour Analysis Services (MSOLAP DLL) est une bibliothèque cliente native. Bibliothèques clientes sont les mêmes pour SQL Server Analysis Services et Azure Analysis Services.
  
##  <a name="bkmk_downloadsite"></a> Où obtenir des versions plus récentes  
 La version installée sur un ordinateur client doit correspondre à la version principale du serveur qui fournit les données. Si l'installation du serveur est plus récente que les fournisseurs de données installés sur les stations de travail de votre réseau, vous devrez peut-être installer les dernières bibliothèques disponibles.  

Bibliothèques clientes incluses dans antérieures de SQL Server Feature Packs correspondent à cette version SQL ; Toutefois, ils peuvent être pas la dernière version. Connexion à Azure Analysis Services peut-être nécessiter des versions ultérieures. Toutes les versions sont à compatibilité descendante.

Pour obtenir la dernière version, consultez [les bibliothèques clientes pour la connexion à Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
