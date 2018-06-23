---
title: Espace de travail de base de données (SSAS tabulaire) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 662daf08-a514-44a7-8675-44644aa454a2
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5a52eb01f176eddd8e69dcdc14609c3776bd54a1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045032"
---
# <a name="workspace-database-ssas-tabular"></a>Base de données d'espace de travail (SSAS Tabulaire)
  La base de données de l'espace de travail de modèles tabulaires, utilisée lors de la création d'un modèle, est créée lorsque vous créez un projet de modèle tabulaire dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. La base de données de l’espace de travail réside en mémoire sur une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s’exécutant en mode tabulaire, en général sur le même ordinateur que [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
 Cette rubrique comprend les sections suivantes :  
  
-   [Présentation de base de données d’espace de travail](#bkmk_overview)  
  
-   [Propriétés de base de données d’espace de travail](#bkmk_ws_prop)  
  
-   [À l’aide de SSMS pour gérer la base de données de l’espace de travail](#bkmk_use_ssms)  
  
-   [Tâches associées](#bkmk_related_tasks)  
  
##  <a name="bkmk_overview"></a> Présentation de base de données d’espace de travail  
 Une base de données d'espace de travail est créée sur l'instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , spécifiée dans la propriété Serveur d'espace de travail, lorsque vous créez un projet Business Intelligence à l'aide de l'un des modèles de projet de modèle tabulaire de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Chaque projet de modèle tabulaire possède sa propre base de données d'espace de travail. Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour afficher la base de données de l'espace de travail sur le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Le nom de la base de données de l'espace de travail inclut le nom du projet, suivi d'un trait de soulignement, du nom d'utilisateur, d'un trait de soulignement et d'un identifiant GUID.  
  
 La base de données de l’espace de travail réside en mémoire tandis que le projet de modèle tabulaire est ouvert dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Lorsque vous fermez le projet, la base de données de l'espace de travail est maintenue en mémoire, stockée sur le disque et supprimée de la mémoire (valeur par défaut), ou supprimée de la mémoire, mais pas stockée sur un disque, comme déterminé par la propriété Rétention de l'espace de travail. Pour plus d'informations sur la propriété Rétention de l'espace de travail, consultez [Propriétés de la base de données de l'espace de travail](#bkmk_ws_prop) plus loin dans cette rubrique.  
  
 Après avoir ajouté des données à votre projet de modèle à l'aide de l'Assistant Importation de table ou des commandes Copier/Coller, lorsque vous affichez les tables, les colonnes et les données dans le générateur de modèles, vous affichez la base de données de l'espace de travail. Si vous ajoutez d’autres tables, colonnes, relations, etc., vous modifiez également la base de données de l’espace de travail.  
  
> [!IMPORTANT]  
>  Si l'une des tables de votre modèle contient un grand nombre de lignes, envisagez d'importer uniquement un sous-ensemble des données lors de la création du modèle. En important un sous-ensemble des données, vous pouvez réduire le temps de traitement et la consommation des ressources du serveur de base de données de l'espace de travail.  
  
> [!NOTE]  
>  La fenêtre d'aperçu dans la page Sélectionner des tables et des vues de l'Assistant Importation de table, la boîte de dialogue Modifier les propriétés de la table et la boîte de dialogue Gestionnaire de partitions affiche les tables, colonnes et lignes au niveau de la source de données, et peut ne pas afficher les mêmes tables, colonnes et lignes que la base de données de l'espace de travail.  
  
 Lorsque vous déployez un projet de modèle tabulaire, la base de données model déployée, qui est en fait une copie de la base de données de l'espace de travail, est créée sur l'instance de serveur Analysis Services spécifiée dans la propriété Serveur de déploiement. Pour plus d’informations sur la propriété Serveur de déploiement, consultez [Propriétés de projet &#40;SSAS Tabulaire&#41;](properties-ssas-tabular.md).  
  
 La base de données model de l'espace de travail réside généralement sur localhost ou sur une instance nommée local d'un serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Vous pouvez utiliser une instance distante de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour héberger la base de données de l'espace de travail ; toutefois, cette configuration n'est pas recommandée en raison de la latence au cours des requêtes de données et d'autres restrictions. De façon optimale, l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui hébergera les bases de données de l'espace de travail se trouve sur le même ordinateur que [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. La création de projets de modèle sur le même ordinateur que l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui héberge la base de données de l'espace de travail peut améliorer les performances.  
  
 Les bases de données d'espace de travail distantes présentent les restrictions suivantes :  
  
-   Latence potentielle pendant les requêtes.  
  
-   La propriété Sauvegarde de données ne peut pas être définie sur **Sauvegarder sur disque**.  
  
-   Vous ne pouvez pas importer de données d'un classeur PowerPivot en créant un projet de modèle tabulaire à l'aide du modèle de projet Importer à partir de PowerPivot.  
  
##  <a name="bkmk_ws_prop"></a> Propriétés de la base de données de l'espace de travail  
 Les propriétés de base de données d'espace de travail sont incluses dans les propriétés du modèle. Pour afficher les propriétés du modèle, dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], dans l' **Explorateur de solutions**, cliquez sur le fichier **Model.bim** . Les propriétés de modèle peuvent être configurées à l'aide de la fenêtre **Propriétés** . Les propriétés spécifiques de la base de données de l'espace de travail sont les suivantes :  
  
> [!NOTE]  
>  Les propriétés**Serveur d'espace de travail**, **Rétention de l'espace de travail**et **Sauvegarde des données** ont des paramètres par défaut qui sont appliqués lorsque vous créez un projet de modèle. Vous pouvez modifier les paramètres par défaut pour les nouveaux projets de modèle dans la page **Modélisation des données** dans les paramètres **Serveur d’analyse** de la boîte de dialogue Outils\Options. Ces propriétés, ainsi que d'autres, peuvent également être définies pour chaque projet de modèle dans la fenêtre **Propriétés** . La modification des paramètres par défaut ne s'applique pas aux projets de modèles déjà créés. Pour plus d’informations, consultez [Configurer les propriétés par défaut de modélisation des données et de déploiement &#40;SSAS Tabulaire&#41;](configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).  
  
|Propriété|Paramètre par défaut|Description|  
|--------------|---------------------|-----------------|  
|**Base de données d’espace de travail**|Nom du projet, suivi d'un trait de soulignement, du nom d'utilisateur, d'un trait de soulignement et d'un identifiant GUID.|Nom de la base de données d'espace de travail utilisée pour le stockage et la modification du projet de modèle en mémoire. Après qu'un projet de modèle tabulaire a été créé, cette base de données apparaît dans l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] spécifiée dans la propriété **Serveur d'espace de travail** . Cette propriété ne peut pas être définie dans la fenêtre Propriétés.|  
|**Rétention de l'espace de travail**|Décharger en mémoire|Spécifie comment une base de données d'espace de travail est conservée une fois que le projet de modèle a été fermé. Une base de données d'espace de travail inclut les métadonnées du modèle et des données importées. Dans certains cas, la base de données d'espace de travail peut être très volumineuse et consommer une grande quantité de mémoire. Par défaut, lorsque vous fermez un projet de modèle dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], la base de données de l'espace de travail est déchargée de la mémoire. Lors de la modification de ce paramètre, il est important de considérer vos ressources mémoire disponibles ainsi que la fréquence à laquelle vous projetez de travailler sur le projet de modèle. Ce paramètre de propriété a les options suivantes :<br /><br /> **Conserver en mémoire** - Indique de conserver la base de données de l’espace de travail en mémoire une fois un projet de modèle fermé. Cette option consomme davantage de mémoire ; toutefois, lors de l'ouverture d'un projet de modèle dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], moins de ressources sont consommées et la base de données de l'espace de travail se charge plus rapidement.<br /><br /> **Décharger de la mémoire** - Indique de conserver la base de données de l’espace de travail sur le disque, mais plus en mémoire, une fois un projet de modèle fermé. Cette option consomme moins de mémoire ; toutefois, lors de l’ouverture d’un projet de modèle dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], la base de données de l’espace de travail doit être à nouveau attachée ; des ressources supplémentaires sont consommées et le projet de modèle se charge plus lentement que si la base de données de l’espace de travail est conservée en mémoire. Utilisez cette option lorsque les ressources en mémoire sont limitées ou lorsque vous travaillez sur une base de données d'espace de travail distante.<br /><br /> **Supprimer l’espace de travail** - Indique de supprimer la base de données de l’espace de travail de la mémoire et de ne pas la garder sur le disque une fois le projet de modèle fermé. Cette option consomme moins de mémoire et d’espace de stockage ; toutefois, lors de l’ouverture d’un projet de modèle dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], des ressources supplémentaires sont consommées et le projet de modèle se charge plus lentement que si la base de données de l’espace de travail est conservée en mémoire ou sur le disque. Utilisez cette option uniquement si vous travaillez occasionnellement sur les projets de modèle.<br /><br /> <br /><br /> Le paramètre par défaut de cette propriété peut être modifié dans la page **Modélisation des données** dans les paramètres **Serveur d’analyse** de la boîte de dialogue Outils\Options.|  
|**Serveur d'espace de travail**|localhost|Cette propriété indique le serveur par défaut qui sera utilisé pour héberger la base de données de l'espace de travail tandis que le projet de modèle est créé dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Toutes les instances disponibles d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui fonctionnent sur l'ordinateur local sont incluses dans la zone de liste.<br /><br /> Pour spécifier un autre serveur de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (s'exécutant en mode tabulaire), tapez le nom de ce serveur. L'utilisateur connecté doit être un administrateur sur le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .<br /><br /> Notez qu’il est recommandé de spécifier une variable locale [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] serveur que le serveur d’espace de travail. Pour les bases de données d'espace de travail sur un serveur distant, l'importation de PowerPivot n'est pas prise en charge, les données ne peuvent pas être sauvegardées localement et l'interface utilisateur peut connaître une latence pendant les requêtes.<br /><br /> Notez également que le paramètre par défaut de cette propriété peut être modifié dans la page modélisation des données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] paramètres dans la boîte de dialogue.|  
  
##  <a name="bkmk_use_ssms"></a> Utilisation de SSMS pour gérer la base de données de l'espace de travail  
 Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) pour vous connecter au serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui héberge la base de données de l'espace de travail. En général, aucune gestion de base de données de l'espace de travail n'est nécessaire ; le détachement ou la suppression d'une base de données de l'espace de travail constitue l'exception et cette opération doit être effectuée dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!WARNING]  
>  N'utilisez pas [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour gérer la base de données de l'espace de travail alors que le projet est ouvert dans le générateur de modèles. Vous risqueriez de perdre des données.  
  
##  <a name="bkmk_related_tasks"></a> Tâches associées  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Propriétés de modèle &#40;SSAS tabulaire&#41;](model-properties-ssas-tabular.md)|Fournit des descriptions et les étapes de configuration des propriétés de base de données de l'espace de travail d'un modèle.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés de déploiement et de la modélisation des données par défaut &#40;SSAS tabulaire&#41;](configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [Propriétés de projet &#40;SSAS tabulaire&#41;](properties-ssas-tabular.md)  
  
  