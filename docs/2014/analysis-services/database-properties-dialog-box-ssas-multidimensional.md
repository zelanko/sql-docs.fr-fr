---
title: Boîte de dialogue Propriétés de la base de données (SSAS-multidimensionnel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.databaseproperties.f1
ms.assetid: 70f000b7-917f-4699-b142-7a0d13ff767c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: be4133aa143ecf0e1fb9b50c40a38a73b4207f30
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082323"
---
# <a name="database-properties-dialog-box-ssas---multidimensional"></a>Boîte de dialogue Propriétés de la base de données (SSAS - Multidimensionnelle)
  Utilisez la boîte de dialogue **Propriétés de la base de données** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour définir les propriétés d'une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Vous pouvez afficher la boîte de dialogue **Propriétés de la base de données** en cliquant avec le bouton droit sur une base de données dans l’Explorateur d’objets et en sélectionnant **Propriétés**.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Nom**|Entrez un nouveau nom pour changer le nom de la base de données.|  
|**IDENTIFI**|Affiche l'identificateur de la base de données.|  
|**Description**|Entrez une nouvelle description pour changer la description de la base de données.|  
|**Créer un horodateur**|Affiche la date et l'heure de création de la base de données.|  
|**Dernière mise à jour du schéma**|Affiche la date et l'heure de la dernière mise à jour des métadonnées de la base de données.|  
|**Dernière mise à jour**|Affiche la date et l'heure de la dernière mise à jour des données de la base de données.|  
|**Informations d'emprunt d'identité de source de données**|Sélectionnez les informations d'emprunt d'identité qu'utilise la base de données lors de la connexion et de l'interaction avec les sources de données contenues dans la base de données. Les valeurs valides sont les suivantes :<br /><br /> **ImpersonateAccount** (utiliser un nom d’utilisateur et un mot de passe Windows spécifiques).<br /><br /> **ImpersonateService** (utiliser le compte de service).<br /><br /> **ImpersonateCurrentUser** (utiliser les informations d’identification de l’utilisateur actuel).<br /><br /> **Par défaut** (utiliser le compte de service pour les opérations MOLAP et l’utilisateur actuel pour l’exploration de données).<br /><br /> Bien que vous puissiez définir les paramètres d'emprunt d'identité de source de données au niveau de la base de données, cela affecte uniquement les sources de données qui spécifient **Hériter** pour leurs paramètres d'emprunt d'identité. Les paramètres d'emprunt d'identité spécifiés directement sur la source de données remplaceront toujours les paramètres spécifiés au niveau de la base de données.<br /><br /> En choisissant une option d'emprunt d'identité, tenez compte des types d'opérations qui devront être prises en charge. Certaines opérations, telles que le traitement, ne peuvent pas être exécutées par|  
|**Dernier traitement**|Affiche la date et l'heure du dernier traitement de la base de données.|  
|**Taille estimée**|Affiche la taille estimée de la base de données.|  
|**Emplacement de stockage**|Spécifie l'emplacement de la base de données. Si la base de données se trouve dans le répertoire de données par défaut, cette valeur sera vide.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Bases de données de modèle multidimensionnels &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
