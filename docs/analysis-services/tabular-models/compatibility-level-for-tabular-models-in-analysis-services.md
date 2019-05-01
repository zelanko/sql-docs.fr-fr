---
title: Niveau de compatibilité pour les modèles tabulaires dans Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd70a673744d2e401e8a28f6ce2c533434e1c75e
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63472312"
---
# <a name="compatibility-level-for-analysis-services-tabular-models"></a>Niveau de compatibilité pour les modèles tabulaires Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Le *niveau de compatibilité* fait référence aux comportements spécifiques à chaque version dans le moteur Analysis Services. Par exemple, DirectQuery et les métadonnées d’objet tabulaire ont des implémentations différentes selon le niveau de compatibilité. En général, vous devez choisir le dernier niveau de compatibilité pris en charge par vos serveurs.

  **Le dernier niveau de compatibilité est 1400** 
  
Principales fonctionnalités dans le niveau de compatibilité 1400 sont les suivantes :

*  Nouvelle infrastructure pour la connectivité des données et les importer dans les modèles tabulaires avec prise en charge de TOM APIs et des scripts TMSL. Cela permet la prise en charge des sources de données supplémentaires telles que le stockage Blob Azure. Données supplémentaires sources seront inclus dans de futures mises à jour.
*  Transformation des données et des fonctionnalités de mashup des données en utilisant des expressions M et obtenir des données dans SSDT.
*  Mesures prennent désormais en charge une propriété de lignes de détails avec une expression DAX, l’activation des outils décisionnels comme Microsoft Excel zoom aux données détaillées à partir d’un rapport agrégé. Par exemple, lorsque les utilisateurs finaux afficher le total des ventes pour une région et un mois, ils peuvent afficher les détails de la commande associée. 
*  Sécurité au niveau objet pour les noms de table et de colonne, en plus des données qu’ils contiennent.
*  Prise en charge améliorée pour les hiérarchies irrégulières.
*  Analyse des performances et améliorations.

  
## <a name="supported-compatibility-levels-by-version"></a>Niveaux de compatibilité pris en charge par version
  
|||  
|-|-|- 
|**Niveau de compatibilité**|**Version du serveur**| 
|1400|Azure Analysis Services, SQL Server 2017 |  
|1200|Azure Analysis Services, SQL Server 2017, SQL Server 2016| 
|1103|SQL Server 2017 *, SQL Server 2016, SQL Server 2014, SQL Server 2012 SP1|  
|1100|SQL Server 2017 *, SQL Server 2016, SQL Server 2014, SQL Server 2012 SP1, SQL Server 2012| 

\* niveaux de compatibilité 1100 et 1103 sont déconseillées dans SQL Server 2017.
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Niveau de compatibilité d’une base de données multidimensionnelle](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [What's new in Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Créez un projet de modèle tabulaire](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  
