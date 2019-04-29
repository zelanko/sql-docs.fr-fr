---
title: Table de mise en lots des membres consolidés (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], attributes staging table
- attributes staging table [Master Data Services]
ms.assetid: 070681ed-be99-49ae-93bd-6402f2134ace
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: bcb553e6762580c20aa3fc126f2f1576d1d5ff68
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925506"
---
# <a name="consolidated-member-staging-table-master-data-services"></a>Table de mise en lots des membres consolidés (Master Data Services)
  Utilisez la table de mise en lots des membres consolidés (stg.name_Consolidated) dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] pour créer, mettre à jour, désactiver et supprimer des membres consolidés. Elle permet également de mettre à jour les valeurs d'attribut des membres consolidés.  
  
##  <a name="TableColumns"></a> Colonnes de table  
 Le tableau suivant explique la fonction de chacun des champs de la table de mise en lots Consolidé.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|**ID**|Identificateur automatiquement affecté. N'entrez pas de valeur dans ce champ. Si le lot n'a pas été traité, ce champ est vide.|  
|**ImportType**<br /><br /> Requis|Détermine ce qu'il convient de faire lorsque les données mises en lots correspondent aux données qui existent déjà dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> **0**: créer des membres. Remplacez les données MDS existantes par les données mises en lots, mais uniquement si les données mises en lots n’ont pas la valeur NULL. Les valeurs NULL sont ignorées. Pour modifier la valeur d’un attribut en NULL, utilisez **~NULL~**.<br /><br /> **1**: créer des nouveaux membres uniquement. Toutes les mises à jour des données MDS existantes échouent.<br /><br /> **2**: créer des membres. Remplacez les données MDS existantes par les données mises en lots. Si vous importez des valeurs NULL, elles remplacent les valeurs MDS existantes.<br /><br /> **3**: désactiver le membre, en fonction de la valeur Code. Les attributs, les appartenances de hiérarchie et de collection et les transactions sont tous conservés mais ne sont plus disponibles dans l'interface utilisateur. Si le membre est utilisé comme valeur d'attribut basé sur un domaine d'un autre membre, la désactivation échoue.<br /><br /> **4** : supprimer définitivement le membre, en fonction de la valeur Code. Les attributs, les appartenances de hiérarchie et de collection et les transactions sont tous supprimés définitivement. Si le membre est utilisé comme valeur d'attribut basé sur un domaine d'un autre membre, la suppression échoue.|  
|**ImportStatus_ID**<br /><br /> Requis|État du processus d'importation. Les valeurs possibles sont :<br /><br /> **0**, que vous spécifiez pour indiquer que l'enregistrement est prêt pour la mise en lots ;<br /><br /> **1**, qui est affecté automatiquement et qui indique que le processus de mise en lots pour l'enregistrement a réussi ;<br /><br /> **2**, qui est affecté automatiquement et qui indique que le processus de mise en lots pour l'enregistrement a échoué.|  
|**Batch_ID**<br /><br /> Requis par le service Web uniquement|Identificateur automatiquement affecté qui regroupe des enregistrements pour la mise en lots. Cet identificateur, affiché dans l'interface utilisateur [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] dans la colonne **ID** , est affecté à tous les membres du lot.<br /><br /> Si le lot n'a pas été traité, ce champ est vide.|  
|**BatchTag**<br /><br /> Requis, sauf par le service Web|Nom unique du lot, jusqu'à 50 caractères.|  
|**HierarchyName**<br /><br /> Requis|Nom de hiérarchie explicite. Chaque membre consolidé ne peut appartenir qu'à une seule hiérarchie.|  
|**ErrorCode**|Affiche un code d'erreur. Pour tous les enregistrements dont la valeur **ImportStatus_ID** est **2**, consultez [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md).|  
|**Code**<br /><br /> Obligatoire, sauf quand les codes sont générés automatiquement pour **ImportType1** ou **2**. Pour plus d’informations, consultez [Création automatique de code &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md).|Code unique du membre.|  
|**Nom**<br /><br /> Ce paramètre est facultatif|Nom du membre.|  
|**NewCode**|À utiliser uniquement si vous modifiez le code du membre.|  
|\<Nom de l’attribut>|Il existe une colonne pour chaque attribut dans l'entité. Utilisez ceci avec un **ImportType** de valeur **0** ou **2**. Pour les attributs de forme libre, spécifiez le nouveau texte ou la nouvelle valeur de chaîne pour l'attribut. Pour les attributs basés sur un domaine, spécifiez le code du membre qui sera l'attribut. Pour les attributs de lien, l'URL doit commencer par **http://**.<br /><br /> Remarque : Vous ne pouvez pas mettre en lots des attributs de fichier.|  
  
## <a name="see-also"></a>Voir aussi  
 [Charger ou mettre à jour des membres dans Master Data Services à l’aide du processus de site](add-update-and-delete-data-master-data-services.md)   
 [Déplacer des membres de hiérarchie explicite à l’aide du processus de site &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Importation de données &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Afficher les erreurs qui se produisent pendant le processus de mise en lots &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md)  
  
  
