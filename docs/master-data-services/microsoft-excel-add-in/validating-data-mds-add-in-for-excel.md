---
title: "Validation des donn&#233;es (Compl&#233;ment MDS pour Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Validation des donn&#233;es (Compl&#233;ment MDS pour Excel)
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], lorsque vous publiez des données, deux types de validation ont lieu :  
  
-   Toutes les règles d'entreprise définies sont appliquées aux données.  
  
-   Les données sont comparées aux valeurs d'attribut autorisées (par exemple, le nombre de caractères ou le type de données).  
  
 Dans chaque cas, les données valides sont publiées dans le référentiel MDS. Les données non valides sont mises en surbrillance et les détails de l'erreur peuvent être affichés dans les colonnes d'état.  
  
## Lorsque la validation a lieu  
 Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], la validation a lieu lorsque vous publiez des données nouvelles ou modifiées, ou lorsque vous appliquez manuellement des règles d'entreprise.  
  
 Lorsque les règles d'entreprise échouent, les données sont tout de même publiées dans le référentiel MDS. Lorsque la validation d'entrée échoue, les données ne sont pas publiées dans le référentiel.  
  
## États de validation  
 Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], les états de validation suivants sont possibles.  
  
 Pour plus d’informations sur les autres états, consultez [Statuts de validation &#40;Master Data Services&#41;](../../master-data-services/validation-statuses-master-data-services.md)  
  
|État|Description|  
|------------|-----------------|  
|Échec de la validation|Une ou plusieurs valeurs dans la ligne n'ont pas pu être validées par rapport aux règles d'entreprise définies par un administrateur MDS.|  
|Validation réussie|Toutes les valeurs dans la ligne ont réussi la validation par rapport aux règles d'entreprise.|  
  
## États d'entrée  
 Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], les états d’entrée suivants sont possibles :  
  
|État|Description|  
|------------|-----------------|  
|Erreur|Une ou plusieurs valeurs dans la ligne ne répondent pas à la configuration requise, notamment en termes de longueur ou de type de données. La valeur n'est pas mise à jour dans le référentiel MDS.|  
|Nouvelle ligne|Les valeurs dans la ligne n'ont pas encore été publiées dans le référentiel MDS.|  
|Lecture seule|L'utilisateur connecté dispose d'autorisations en lecture seule sur une ou plusieurs valeurs dans la ligne et les valeurs ne peuvent pas être mises à jour.|  
|Inchangé|Aucune valeur dans la ligne n'a été modifiée dans la feuille de calcul. Cela ne signifie pas que les valeurs contenues dans le référentiel n’ont pas changé ; pour obtenir les données les plus récentes dans la feuille, dans le groupe **Se connecter et charger** , cliquez **Charger ou actualiser**.<br /><br /> Il s'agit du paramètre par défaut pour chaque ligne.|  
  
## Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Déterminez les valeurs qui ne respectent pas les règles d'entreprise définies.|[Appliquer des règles d’entreprise &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
|Pour aider à corriger les erreurs de validation, affichez toutes les transactions qui ont eu lieu pour un membre.|[Afficher toutes les annotations ou transactions pour un membre &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## Contenu connexe  
  
-   [Vue d’ensemble : importation de données à partir d’Excel &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  