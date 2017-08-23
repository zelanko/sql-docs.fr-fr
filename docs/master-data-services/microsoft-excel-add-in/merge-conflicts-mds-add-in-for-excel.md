---
title: "Fusionner les conflits (complément MDS pour Excel) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf95978f-a2c5-4325-8606-dbd4e88741b8
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4ede349c35ea8bd25d81b42e6240c6c7a7ebdab9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="merge-conflicts-mds-add-in-for-excel"></a>Fusionner les conflits (complément MDS pour Excel)
  Dans le complément [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] pour Excel, si les données ont été modifiées sur le serveur par un utilisateur, la publication échoue, avec une erreur de conflit. Pour résoudre cette erreur, vous pouvez exécuter la fonctionnalité Conflits de fusion et publier à nouveau les modifications.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   Vous devez disposer au minimum d’une autorisation de mise à jour sur l’objet de modèle feuille de l’entité que vous êtes en train de mettre à jour.  
  
-   La feuille de calcul active doit inclure des données gérées par MDS.  
  
-   La feuille de calcul active doit présenter une erreur de conflit lorsque vous tentez de publier vos modifications.  
  
### <a name="to-merge-conflicts"></a>Pour fusionner des conflits  
  
1.  Dans la feuille de calcul, sélectionnez la ligne ou la cellule qui présente une erreur de conflit.  
  
2.  Dans le groupe de menus **Publier et valider** , sélectionnez **Fusionner les conflits** pour ouvrir la boîte de dialogue **Fusionner les conflits** .  
  
3.  Dans la boîte de dialogue **Fusionner les conflits** , vous pouvez effectuer l’une des opérations suivantes :  
  
    -   Choisissez **Dernière** et cliquez sur **Appliquer** si vous voulez annuler les modifications en attente et recharger la dernière version à partir du serveur.  
  
    -   Choisissez **Initiale** et cliquez sur **Appliquer** si vous souhaitez appliquer la version d’origine dans la feuille de calcul.  
  
    -   Choisissez **Les vôtres** et cliquez sur **Appliquer** pour conserver les modifications locales existantes.  
  
4.  Après avoir cliqué sur **Appliquer**, vous pouvez apporter des modifications supplémentaires et réeffectuer la publication. Vous pouvez également cliquer sur **Annuler** si vous souhaitez annuler la mise à jour et recharger la dernière version à partir du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : importation de données à partir d’Excel &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
