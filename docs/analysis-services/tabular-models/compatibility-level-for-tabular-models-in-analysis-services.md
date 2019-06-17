---
title: Niveau de compatibilité pour les modèles tabulaires dans Analysis Services | Microsoft Docs
ms.date: 06/10/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19c69aa1a1ab27e7498d3c9d6a0d52c25b9f0020
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66826830"
---
# <a name="compatibility-level-for-analysis-services-tabular-models"></a>Niveau de compatibilité pour les modèles tabulaires Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Le *niveau de compatibilité* fait référence à des améliorations de fonctionnalités et de fonctionnalités dans le moteur Analysis Services, ainsi que dans les métadonnées de modèle tabulaire. En général, vous devez choisir le dernier niveau de compatibilité pris en charge par vos serveurs. 

  **Le dernier niveau de compatibilité pris en charge est 1400** 
  
Principales fonctionnalités dans le niveau de compatibilité 1400 sont les suivantes :

*  Nouvelle infrastructure pour la connectivité des données et les importer dans les modèles tabulaires avec prise en charge de TOM APIs et des scripts TMSL. Cela permet la prise en charge des sources de données supplémentaires telles que le stockage Blob Azure. Données supplémentaires sources seront inclus dans de futures mises à jour.
*  Transformation des données et des fonctionnalités de mashup des données à l’aide d’expressions M et obtenir des données dans SQL Server Data Tools (SSDT).
*  Mesure maintenant la prise en charge une propriété de lignes de détails avec une expression DAX, activer une analyse Décisionnelle des outils tels que de simulation de Microsoft Excel pour les données à partir d’un rapport agrégé détaillées. Par exemple, lorsque les utilisateurs consultent le total des ventes pour une région et un mois, ils peuvent afficher les détails de la commande associée. 
*  Sécurité au niveau objet pour les noms de table et de colonne, en plus des données qu’ils contiennent.
*  Prise en charge améliorée pour les hiérarchies irrégulières.
*  Analyse des performances et améliorations.

  
## <a name="supported-compatibility-levels-by-version"></a>Niveaux de compatibilité pris en charge par version
  
Niveaux de compatibilité inférieurs sont prises en charge vers l’arrière compatibilité. 

|||  
|-|-|- 
|**Niveau de compatibilité**|**Version du serveur**| 
|1470|SQL Server 2019 (CTP 2.3 et versions ultérieures) | 
|1400|Azure Analysis Services, SQL Server 2019, SQL Server 2017 |  
|1200|Azure Analysis Services, SQL Server 2019, SQL Server 2017, SQL Server 2016| 
|1103|SQL Server 2017 *, SQL Server 2016, SQL Server 2014, SQL Server 2012 SP1|  
|1100|SQL Server 2017 *, SQL Server 2016, SQL Server 2014, SQL Server 2012 SP1, SQL Server 2012| 

\* niveaux de compatibilité 1100 et 1103 sont déconseillées dans SQL Server 2017 et versions ultérieures.
  
## <a name="set-compatibility-level"></a>Définir un niveau de compatibilité 
 Lorsque vous créez un nouveau projet de modèle tabulaire dans SQL Server Data Tools (SSDT), vous pouvez spécifier le niveau de compatibilité sur les **Générateur de modèles tabulaires** boîte de dialogue. 
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.png)  
  
 Si vous sélectionnez le **ne plus afficher ce message** option, tous les projets suivants utilise le niveau de compatibilité que vous avez spécifié comme la valeur par défaut. Vous pouvez modifier le niveau de compatibilité par défaut dans SSDT sous **Outils** > **Options**.  
  
 Pour mettre à niveau un projet de modèle tabulaire dans SSDT, définissez le **niveau de compatibilité** propriété dans le modèle **propriétés** fenêtre. Gardez à l’esprit, la mise à niveau le niveau de compatibilité est irréversible.
  
## <a name="check-compatibility-level-for-a-database-in-ssms"></a>Vérifier le niveau de compatibilité d'une base de données dans SSMS  
 Dans SSMS, cliquez sur le nom de la base de données > **propriétés** > **niveau de compatibilité**.  
  
## <a name="check-supported-compatibility-level-for-a-server-in-ssms"></a>Vérifier le niveau de compatibilité pris en charge pour un serveur dans SSMS  
 Dans SSMS, cliquez avec le bouton droit sur le nom du serveur, puis choisissez **Propriétés** > **Niveau de compatibilité pris en charge**.  

 Cette propriété spécifie le niveau de compatibilité le plus élevé d’une base de données qui s’exécutera sur le serveur. Le niveau de compatibilité pris en charge est en lecture seule et ne peut pas être modifié.
 
> [!NOTE]  
>  Dans SSMS, cas de connexion à un serveur SQL Server Analysis Services, le serveur Azure Analysis Services ou l’espace de travail Power BI Premium, la propriété de niveau de compatibilité pris en charge affichera 1200. Il s’agit d’un problème connu et sera résolu dans une prochaine SSMS mise à jour. Une fois résolu, cette propriété apparaît le plus haut niveau de compatibilité pris en charge. 
  
## <a name="see-also"></a>Voir aussi  
 [Niveau de compatibilité d’une base de données multidimensionnelle](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [What's new in Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Créez un projet de modèle tabulaire](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  
