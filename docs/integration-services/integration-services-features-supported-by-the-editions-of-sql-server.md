---
title: "Fonctionnalités prises en charge par les éditions de SQL Server Integration Services | Documents Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 8cc1fcfdeae8742a93916dfb08c9db1215f88721
ms.openlocfilehash: e9d1b8851f113fa44264230a79d0e496007ed96b
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="integration-services-features-supported-by-the-editions-of-sql-server"></a>Fonctionnalités Integration Services pris en charge par les éditions de SQL Server
 Cette rubrique fournit des détails sur les fonctionnalités de SQL Server Integration Services (SSIS) prises en charge par les différentes éditions de [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].  

Pour les fonctionnalités prises en charge par les éditions Evaluation et Developer, consultez les fonctionnalités répertoriées pour Enterprise Edition dans les tableaux suivants.
  
Pour les dernières notes et informations sur les nouveautés, consultez les articles suivants :
-   [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
-   [Nouveautés d’Integration Services dans SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [Nouveautés d’Integration Services dans SQL Server 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)
    
**Essayez SQL Server 2016 !**    

La version d’évaluation de SQL Server est disponible pendant une période d’évaluation de 180 jours.  
    
> [![Télécharger à partir du Centre d’évaluation](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Télécharger SQL Server 2016 à partir du Centre d’évaluation](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
## <a name="ISNew"></a>Nouvelles fonctionnalités d’Integration Services dans SQL Server 2017
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Montée en puissance parallèle principale|Oui|||||
|Montée en charge de travail|Oui|Oui <sup>1</sup>|TBD|TBD|TBD|
|Prise en charge pour Microsoft Dynamics AX et Microsoft Dynamics CRM dans les composants d’OData <sup>2</sup>|Oui|Oui||||

<sup>1</sup> si vous exécutez des packages qui nécessitent des fonctionnalités d’entreprise uniquement de monter en charge, la mise à l’échelle des travailleurs doit également exécuter sur des instances de SQL Server Enterprise.

<sup>2</sup> cette fonctionnalité est également pris en charge dans SQL Server 2016 avec Service Pack 1.

## <a name="IEWiz"></a>SQL Server Assistant Importation et exportation

|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Assistant Importation et Exportation SQL Server|Oui|Oui|Oui|Oui|Oui|  

## <a name="IS"></a> Integration Services  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Connecteurs de source de données intégrés|Oui|Oui|||| 
|Tâches et transformations intégrées|Oui|Oui||||  
|Source ODBC et la destination par Attunity|Oui|Oui|||| 
|Connecteurs et tâches de sources de données Azure|Oui|Oui||||  
|Tâches et les connecteurs Hadoop/HDFS|Oui|Oui||||  
|Outils de profilage de données de base|Oui|Oui|||| 

## <a name="ISAA"></a>Integration Services - Advanced sources et destinations  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Source d’Oracle de haute performance et de destination par Attunity|Oui|||||  
|Source Teradata de haute performance et de destination par Attunity|Oui|||||  
|Source et destination SAP BW|Oui|||||  
|Destination d’apprentissage du modèle données d’exploration de données|Oui|||||  
|Destination de traitement de dimension|Oui|||||  
|Destination de traitement de partition|Oui|||||  
  
## <a name="ISAT"></a>Integration Services - avancée des tâches et transformations  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Modification des composants de Capture de données par Attunity <sup>1</sup>|Oui|||||  
|Transformation de requête d'exploration de données|Oui|||||  
|Regroupement probable et transformations de recherche floue|Oui|||||  
|Extraction de terme et les transformations de recherche de terme|Oui|||||  

<sup>1</sup> le de Capture de données modifiées par Attunity nécessitent Enterprise edition. Le Service de Capture de données modifiées et le Concepteur de Capture de données modifiées, toutefois, ne requièrent pas Enterprise edition. Vous pouvez utiliser le concepteur et le Service sur un ordinateur où SSIS n’est pas installé.

