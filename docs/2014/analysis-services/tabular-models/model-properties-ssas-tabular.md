---
title: Propriétés de modèle (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.fileprop.f1
- sql12.asvs.bidtoolset.wspacedbconfig.f1
ms.assetid: 8ab04656-75a5-485c-9687-7b1ca49f7f80
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 47ca12ee0118e0c2b63da05cf2d508ec0c2f5f92
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66066954"
---
# <a name="model-properties-ssas-tabular"></a>Propriétés de modèle (SSAS Tabulaire)
  Cette rubrique décrit les propriétés de modèle tabulaire. Chaque projet de modèle tabulaire dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] a des propriétés de modèle qui affectent la façon dont le modèle que vous créez est construit, comment il est sauvegardé et comment la base de données de l'espace de travail est stockée. Les propriétés du modèle décrites ici ne s'appliquent pas aux modèles qui ont déjà été déployés.  
  
 Sections de cette rubrique :  
  
-   [Propriétés de modèle](#bkmk_model_properties)  
  
-   [Pour configurer des paramètres de propriété de modèle](#bkmk_conf)  
  
##  <a name="model-properties"></a><a name="bkmk_model_properties"></a>Propriétés de modèle  
 **Avancé**  
  
|Propriété|Paramètre par défaut|Description|  
|--------------|---------------------|-----------------|  
|**Action de génération**|Compiler|Cette propriété indique comment le fichier est lié au processus de génération et de déploiement. Ce paramètre de propriété a les options suivantes :<br /><br /> **Compiler** -une action de génération normale se produit. Les définitions des objets de modèle sont écrites dans le fichier .asdatabase.<br /><br /> **None** : la sortie dans le fichier. asdatabase est vide.|  
|**Copier dans le répertoire de sortie**|Ne pas copier|Cette propriété indique que le fichier source sera copié dans le répertoire de sortie. Ce paramètre de propriété a les options suivantes :<br /><br /> **Ne pas copier** -aucune copie n’est créée dans le répertoire de sortie.<br /><br /> **Toujours copier** -une copie est toujours créée dans le répertoire de sortie.<br /><br /> **Copier si plus récent** - Une copie est créée dans le répertoire de sortie uniquement si des modifications sont apportées au fichier model.bim.|  
  
 **Divers**  
  
> [!NOTE]  
>  Certaines propriétés sont définies automatiquement lors de la création du modèle et ne peuvent pas être modifiées.  
  
> [!NOTE]  
>  Les propriétés Serveur d'espace de travail, Rétention de l'espace de travail et Sauvegarde des données ont des paramètres par défaut qui sont appliqués lorsque vous créez un projet de modèle. Vous pouvez modifier les paramètres par défaut pour les nouveaux modèles sur la page Modélisation des données dans les paramètres Analysis Server de la boîte de dialogue Outils\Options. Ces propriétés, ainsi que d'autres, peuvent également être définies pour chaque modèle dans la fenêtre Propriétés. Pour plus d’informations, consultez [Configurer les propriétés par défaut de modélisation des données et de déploiement &#40;SSAS Tabulaire&#41;](properties-ssas-tabular.md).  
  
|Propriété|Paramètre par défaut|Description|  
|--------------|---------------------|-----------------|  
|**Classement**|Classement par défaut de l'ordinateur pour lequel Visual Studio est installé.|Indicateur de classement pour le modèle.|  
|**Niveau de compatibilité**|Valeur par défaut ou autre valeur sélectionnée lors de la création du projet.|S"applique à SQL Server 2012 Analysis Services SP1 et aux versions ultérieures. Spécifie les fonctionnalités et les paramètres disponibles pour ce modèle. Pour plus d’informations, consultez [niveau de compatibilité &#40;SSAS tabulaire SP1&#41;](compatibility-level-for-tabular-models-in-analysis-services.md).|  
|**Sauvegarde des données**|Ne pas sauvegarder sur disque|Spécifie si une sauvegarde des données du modèle est conservée dans un fichier de sauvegarde. Notez que le paramètre par défaut de cette propriété peut être modifié sur la page modélisation des données dans Analysis Server paramètres de la boîte de dialogue Outils\options.. Ce paramètre de propriété a les options suivantes :<br /><br /> **Sauvegarder sur disque** - Indique de garder une sauvegarde des données du modèle sur le disque. Lorsque le modèle est enregistré, les données sont également enregistrées dans le fichier de sauvegarde (ABF). La sélection de cette option peut ralentir l'enregistrement du modèle et le temps de chargement.<br /><br /> **Ne pas sauvegarder sur disque** - Indique de ne pas garder de sauvegarde des données du modèle sur le disque. Cette option réduit le temps d'enregistrement et de chargement du modèle.|  
|**Mode DirectQuery**|Désactivé|Spécifie si ce modèle fonctionne en mode DirectQuery. Pour plus d’informations, consultez [Mode DirectQuery &#40;SSAS Tabulaire&#41;](directquery-mode-ssas-tabular.md).|  
|**Nom de fichier**|Model.bim|Spécifie le nom du fichier.bim. Le nom de fichier ne doit pas être modifié.|  
|**Chemin d'accès complet**|Chemin d'accès spécifié lorsque le projet a été créé.|Emplacement du fichier model.bim. Cette propriété ne peut pas être définie dans la fenêtre Propriétés.|  
|**Langage**|Anglais|Langue par défaut du modèle. La langue par défaut est déterminée par la langue de Visual Studio. Cette propriété ne peut pas être définie dans la fenêtre Propriétés.|  
|**Base de données d'espace de travail**|Le nom du projet, suivi d'un trait de soulignement, puis d'un GUID.|Nom de la base de données d'espace de travail utilisée pour le stockage et la modification du modèle en mémoire pour le fichier model.bim sélectionné. Cette base de données apparaît dans l'instance Analysis Services spécifiée dans la propriété Serveur d'espace de travail. Cette propriété ne peut pas être définie dans la fenêtre Propriétés. Pour plus d’informations, consultez [Base de données d’espace de travail &#40;SSAS Tabulaire&#41;](workspace-database-ssas-tabular.md).|  
|**Rétention de l'espace de travail**|Décharger de la mémoire|Spécifie comment une base de données d'espace de travail est conservée une fois que le modèle a été fermé. Une base de données d'espace de travail inclut les métadonnées du modèle, les données importées dans un modèle et les informations d'identification d'emprunt d'identité (chiffrées). Dans certains cas, la base de données d'espace de travail peut être très volumineuse et consommer une quantité significative de mémoire. Par défaut, les bases de données d'espace de travail sont déchargées de la mémoire. Lors de la modification de ce paramètre, il est important de considérer vos ressources mémoire disponibles ainsi que la fréquence à laquelle vous projetez de travailler sur le modèle. Notez que le paramètre par défaut de cette propriété peut être modifié sur la page modélisation des données dans Analysis Server paramètres de la boîte de dialogue Outils\options.. Ce paramètre de propriété a les options suivantes :<br /><br /> **Conserver en mémoire** - Indique de conserver la base de données de l’espace de travail en mémoire une fois le modèle fermé. Cette option consommera plus de mémoire ; toutefois, lors de l'ouverture d'un modèle dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], moins de ressources sont consommées et la base de données de l'espace de travail se chargera plus vite.<br /><br /> **Décharger de la mémoire** - Indique de garder la base de données de l’espace de travail sur le disque, mais pas dans la mémoire, une fois le modèle fermé. Cette option consommera moins de mémoire ; toutefois, lors de l'ouverture d'un modèle dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], des ressources supplémentaires seront consommées et le modèle se chargera plus lentement que si la base de données de l'espace de travail est conservée en mémoire. Utilisez cette option lorsque les ressources en mémoire sont limitées ou lorsque vous travaillez sur une base de données d'espace de travail distante.<br /><br /> **Supprimer l’espace de travail** - Indique de supprimer la base de données de l’espace de travail de la mémoire et de ne pas la garder sur le disque une fois le modèle fermé. Cette option consommera moins de mémoire et d’espace de stockage. Toutefois, lors de l’ouverture d’un modèle dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], des ressources supplémentaires sont consommées et le modèle se charge plus lentement que si la base de données de l’espace de travail est conservée en mémoire ou sur le disque. Utilisez cette option uniquement si vous travaillez occasionnellement sur les modèles.|  
|**Serveur d'espace de travail**|localhost|Cette propriété indique le serveur par défaut qui sera utilisé pour héberger la base de données de l'espace de travail tandis que le modèle est créé dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Toutes les instances disponibles d'Analysis Services qui fonctionnent sur l'ordinateur local sont incluses dans la zone de liste.<br /><br /> Remarque : il est recommandé de toujours spécifier un serveur Analysis Services local en tant que serveur d’espace de travail. Pour les bases de données d'espace de travail sur un serveur distant, l'importation depuis PowerPivot n'est pas prise en charge, les données ne peuvent pas être sauvegardées localement et l'interface utilisateur peut connaître une latence pendant les requêtes.<br /><br /> Le paramètre par défaut de cette propriété peut être modifié sur la page Modélisation des données dans les paramètres Analysis Server de la boîte de dialogue Outils\Options.|  
  
##  <a name="bkmk_conf_model_prop"></a>   
###  <a name="to-configure-model-property-settings"></a><a name="bkmk_conf"></a>Pour configurer les paramètres de propriété de modèle  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans l' **Explorateur de solutions**, cliquez sur le fichier **Model.bim** .  
  
2.  Dans la fenêtre **Propriétés** , cliquez sur une propriété, puis tapez une valeur ou cliquez sur la flèche Bas pour sélectionner une option de paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés de déploiement et de modélisation des données par défaut &#40;SSAS tabulaire&#41;](properties-ssas-tabular.md)   
 [Propriétés de projet &#40;SSAS Tabulaire&#41;](project-properties-ssas-tabular.md)  
  
  
