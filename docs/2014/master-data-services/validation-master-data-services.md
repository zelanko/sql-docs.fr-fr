---
title: Validation (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 0ba00faa58a4ac37c2c1c574000b028333f2bd52
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308019"
---
# <a name="validation-master-data-services"></a>Validation (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les données sont validées pour en garantir l'exactitude. Une partie de la validation s'effectue automatiquement, tandis qu'une autre partie est basée sur des règles d'entreprise créées par les administrateurs.  
  
## <a name="when-data-validation-occurs"></a>Occurrences de la validation des données  
 La validation se produit à différents moments et s'affiche de différentes manières dans l'application Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
|Type de validation|Standards déterminés par|Lorsqu'elle se produit|Affichée dans l'interface utilisateur Web du gestionnaire de MasterData en tant que|Affichée dans le complément pour Excel en tant que|Les données sont-elles enregistrées dans le référentiel MDS ?|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|Validation de la règle d'entreprise|Administrateur MDS|Automatiquement lorsqu'un utilisateur ajoute ou modifie des données.<br /><br /> Manuellement lorsqu'un utilisateur applique des règles d'entreprise.<br /><br /> Manuellement, lorsqu'un administrateur dans la zone fonctionnelle **Gestion des versions** de l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] valide une version par rapport aux règles d'entreprise.|Erreurs de validation|ValidationStatus|Oui|  
|Validation de type de données et de contenu|Un administrateur MDS, en créant des objets de modèle (par exemple, la longueur ou le type de données d'un attribut)|Automatiquement lorsqu'un utilisateur ajoute ou modifie des données.|Erreurs d'entrée|InputStatus|non|  
|Validation de type de données et de contenu|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Automatiquement lorsqu'un utilisateur ajoute ou modifie des données.|Erreurs d'entrée|InputStatus|non|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créer et publier des règles d'entreprise par rapport auxquelles valider des données.|[Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](create-and-publish-a-business-rule-master-data-services.md)|  
|Valider une version des données par rapport aux règles d'entreprise. Administrateurs uniquement.|[Valider une Version par rapport aux règles métier &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)|  
|Valider des sous-ensembles de données spécifiques par rapport aux règles d'entreprise. Tous les utilisateurs autorisés à accéder à la zone fonctionnelle **Explorateur** .|[Valider des membres spécifiques par rapport aux règles métier &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Valider des sous-ensembles de données spécifiques par rapport aux règles d'entreprise. Tous les utilisateurs autorisés à accéder à la zone fonctionnelle **Explorateur** et utilisant [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].|[Appliquer des règles d’entreprise &#40;complément MDS pour Excel&#41;](microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Les règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
