---
title: Chevauchement des autorisations de modèle et de membre (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: dd9706ee95376500993089a496f216c2fe113b27
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144528"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a>Chevauchement des autorisations de modèle et de membre (Master Data Services)
  Une autorisation attribuée à un membre et une autorisation attribuée à un objet de modèle peuvent se chevaucher. Lorsque des chevauchements se produisent, l'autorisation la plus restrictive entre en vigueur.  
  
 Si un membre a une autorisation qui est différente de celle de son objet de modèle correspondant, les règles suivantes s'appliquent :  
  
-   **Refuser** remplace toutes les autres autorisations.  
  
-   **En lecture seule** substitue **mise à jour**.  
  
 L'image suivante montre les autorisations appliquées sur une valeur d'attribut individuelle lorsque les autorisations d'attribut sont différentes des autorisations de membre.  
  
 ![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")  
  
## <a name="example-1"></a>Exemple 1  
 ![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")  
  
 Sous l'onglet **Modèles** , l'entité Product a l'autorisation **Mise à jour** attribuée. Tous les attributs dans l'entité héritent de cette autorisation.  
  
 Sous l'onglet **Membres de hiérarchie** , le nœud de sous-catégorie Mountain Bikes dans une hiérarchie dérivée a l'autorisation **Mise à jour** attribuée.  
  
 Résultat : dans **Explorateur**, l'utilisateur a l'autorisation **Mise à jour** sur toutes les valeurs d'attribut de tous les membres qui se trouvent dans le nœud Mountain Bikes. Tous les autres membres et attributs sont masqués.  
  
 ![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")  
  
## <a name="example-2"></a>Exemple 2  
 ![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")  
  
 Sous l'onglet **Modèles** , l'attribut Subcategory a l'autorisation **Mise à jour** attribuée.  
  
 Sur le **membres de hiérarchie** onglet, le nœud de sous-catégorie Mountain Bikes dans une hiérarchie dérivée est explicitement assigné **en lecture seule** autorisation.  
  
 Résultat : Dans **Explorer**, l’utilisateur a **en lecture seule** autorisation aux valeurs d’attribut Subcategory des membres dans le nœud Mountain Bikes. Tous les autres membres et attributs sont masqués.  
  
 ![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="example-3"></a>Exemple 3  
 ![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")  
  
 Sur le **modèles** onglet, l’attribut Subcategory a **en lecture seule** autorisation affectée.  
  
 Sous l'onglet **Membres de hiérarchie** , le nœud de sous-catégorie Mountain Bikes dans une hiérarchie dérivée a l'autorisation **Mise à jour** attribuée explicitement.  
  
 Résultat : Dans **Explorer**, l’utilisateur a **en lecture seule** autorisation aux valeurs d’attribut. Tous les autres membres et attributs sont masqués.  
  
 ![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les autorisations sont déterminées &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)   
 [Chevauchement des autorisations des utilisateurs et des groupes &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  