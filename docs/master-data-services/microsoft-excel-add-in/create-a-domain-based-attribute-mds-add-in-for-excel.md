---
title: "Créer un attribut basé sur un domaine (complément MDS pour Excel) | Documents Microsoft"
ms.custom: 
ms.date: 07/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b3e30dc-8f41-4a5d-8009-ae5a4426a64b
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f67b43f772e9693f5abbb396b6987527a5220a1d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-domain-based-attribute-mds-add-in-for-excel"></a>Créer un attribut basé sur un domaine (complément MDS pour Excel)
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], les administrateurs peuvent créer un attribut basé sur un domaine quand ils souhaitent limiter les valeurs d’une colonne à un ensemble de valeurs spécifique.  
  
 Les valeurs peuvent déjà figurer dans la feuille de calcul ou provenir d'une entité existante.  
  
> [!NOTE]  
>  Si les utilisateurs tapent une valeur dans la colonne contrainte au lieu de la sélectionner dans la liste, des erreurs sont affichées dans la colonne **$InputStatus$** lors de la publication.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder aux zones fonctionnelles **Administration de système** et **Explorateur** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../../master-data-services/administrators-master-data-services.md).  
  
-   Le modèle et l'entité doivent déjà exister.  
  
### <a name="to-perform-this-procedure"></a>Pour effectuer cette procédure :  
  
1.  Dans Excel, chargez l'entité qui contient la colonne (attribut) que vous souhaitez limiter. Pour plus d’informations, consultez [Exporter des données dans Excel depuis Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
2.  Cliquez sur une cellule de la colonne que vous souhaitez limiter.  
  
3.  Dans le groupe **Modèle de build** , cliquez sur **Propriétés d'attribut**.  
  
4.  Dans la boîte de dialogue **Propriétés d’attribut** , dans la liste **Type d’attribut** , choisissez **Liste contrainte (basée sur un domaine)**.  
  
5.  Dans la liste **Remplir l’attribut avec les valeurs de** :  
  
    -   Pour utiliser des valeurs de la feuille de calcul, choisissez **la colonne sélectionnée**. Une nouvelle entité et une nouvelle table de mise en lots seront créées avec les valeurs de la colonne sélectionnée.  
  
    -   Pour utiliser des valeurs d'une entité existante, choisissez le nom de l'entité.
    
    S’il y a plus de 50 entités, vous pouvez filtrer et rechercher pour une entité. Sinon, sélectionnez une entité dans la liste déroulante.  
  
6.  Si vous avez choisi **la colonne sélectionnée** à l’étape précédente, dans la zone **Nouveau nom d’entité** , tapez un nom pour la nouvelle entité. Il peut être identique au nom de la colonne (attribut).  
  
7.  Cliquez sur **OK**. Chaque cellule dans la colonne comporte désormais une liste de valeurs dans laquelle les utilisateurs peuvent faire leur choix.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Pour ajouter et supprimer des valeurs dans la liste contrainte, chargez l'entité sur laquelle l'attribut est basé. Pour plus d’informations sur le chargement d’entités, consultez [Exporter des données dans Excel depuis Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs basés sur un domaine &#40;Master Data Services&#41;](../../master-data-services/domain-based-attributes-master-data-services.md)   
 [Créer une entité &#40; Complément MDS pour Excel &#41;](../../master-data-services/microsoft-excel-add-in/create-an-entity-mds-add-in-for-excel.md)   
 [Génération d’un modèle &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/building-a-model-mds-add-in-for-excel.md)  
  
  
