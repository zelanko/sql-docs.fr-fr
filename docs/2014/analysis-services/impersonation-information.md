---
title: Les informations d’emprunt d’identité | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42319d60-ccd0-46b8-af0b-f0968c390d8a
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 90a9d2102df9bd1b6cdf2bf1e4c7b3386c0fa825
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041275"
---
# <a name="impersonation-information"></a>Informations d’emprunt d’identité
  Utilisez la page **Informations d’emprunt d’identité** pour spécifier les informations d’identification qu’Analysis Services utilisera pour se connecter à la source de données.  
  
## <a name="options"></a>Options  
 **Utiliser un nom d’utilisateur Windows spécifique et un mot de passe**  
 Sélectionnez cette option pour que l’objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les informations d’identification de sécurité d’un compte d’utilisateur Windows. Les informations d’identification spécifiées sont utilisées pour le traitement, les requêtes ROLAP, les liaisons hors-ligne, les cubes locaux, les modèles d’exploration, les partitions distantes, les objets liés et la synchronisation entre la cible et la source. Cependant, pour les instructions DMX (Data Mining Extensions) OPENQUERY, cette option est ignorée et les informations d’identification de l’utilisateur actuel sont utilisées.  
  
 **Nom d'utilisateur**  
 Tapez le domaine et le nom du compte d'utilisateur que doit utiliser l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sélectionné. Utilisez le format suivant :  
  
 *\<Nom de domaine >* **\\**  *\<nom de compte d’utilisateur >*  
  
 Cette option est activée si **Utiliser un nom d'utilisateur et un mot de passe spécifiques** est sélectionné.  
  
 **Mot de passe**  
 Tapez le mot de passe du compte d'utilisateur que doit utiliser l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sélectionné.  
  
 Cette option est activée si **Utiliser un nom d'utilisateur et un mot de passe spécifiques** est sélectionné.  
  
 **Utiliser le compte de service**  
 Sélectionnez cette option pour que l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les informations d'identification de sécurité associées au service [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui gère l'objet. Les informations d'identification du compte de service sont utilisées pour le traitement, les requêtes ROLAP, les partitions distantes, les objets liés et la synchronisation entre la cible et la source. Cependant, pour les instructions DMX (Data Mining Extensions) OPENQUERY, les cubes locaux et les modèles d'exploration de données, les informations d'identification de l'utilisateur actuel sont utilisées. Cette option n'est pas prise en charge pour les liaisons hors ligne.  
  
 **Utiliser les informations d'identification de l'utilisateur actuel**  
 Sélectionnez cette option afin que l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les informations d'identification de sécurité de l'utilisateur actuel pour les liaisons hors ligne, les instructions DMX OPENQUERY, les cubes locaux et les modèles d'exploration de données. Cette option n'est pas prise en charge pour le traitement, les requêtes ROLAP, les partitions distantes, les objets liés et la synchronisation entre la cible et la source.  
  
 **Hériter de**  
 Sélectionnez cette option pour utiliser le comportement d'emprunt d'identité, défini au niveau de la base de données, qui a été défini par l'administrateur du serveur à l'aide de la propriété de base de données `DataSourceImpersonation`.  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données dans les modèles multidimensionnels](multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Les Sources de données prises en charge &#40;SSAS multidimensionnel&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  