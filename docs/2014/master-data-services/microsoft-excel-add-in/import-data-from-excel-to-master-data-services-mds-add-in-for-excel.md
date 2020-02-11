---
title: Publier des données d’Excel dans MDS (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ffb122b96182b1079c95adf13d26c9a4949f6ddf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65478805"
---
# <a name="publish-data-from-excel-to-mds-mds-add-in-for-excel"></a>Publier des données d'Excel dans MDS (Complément MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous pouvez publier les données dans le référentiel MDS quand vous avez fini de travailler dans Excel et souhaitez enregistrer vos modifications afin que d’autres utilisateurs puissent y accéder.  
  
> [!NOTE]
>  -   Lorsque vous publiez des modifications, les commentaires sur les cellules managées MDS sont supprimés.  
> -   Une formule n'est pas prise en charge dans une cellule managée MDS. Une formule dans une cellule managée MDS est traitée comme valeur de texte.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   La feuille de calcul active doit contenir des données managées MDS et vous devez avoir apporté des modifications ou effectué des ajouts à ces données.  
  
-   Si vous ajoutez des membres, vous ne devez pas spécifier de valeur **Code** si les codes de l'entité sont générés automatiquement. Pour plus d’informations, consultez [création automatique de Code &#40;Master Data Services&#41;](../automatic-code-creation-master-data-services.md).  
  
### <a name="to-publish-data-to-the-mds-repository"></a>Pour publier des données dans le référentiel MDS  
  
1.  Dans le groupe **Publier et valider** , cliquez sur **Publier**.  
  
2.  facultatif. Si la boîte de dialogue **Publier et annoter** s’affiche, choisissez de partager la même annotation (commentaire) pour toutes les mises à jour, ou d’annoter chaque modification individuellement.  
  
3.  facultatif. Activez la case à cocher **Ne plus afficher cette boîte de dialogue** . Vous pouvez toujours afficher la boîte de dialogue ultérieurement en choisissant **Paramètres** et en sélectionnant la case à cocher **Afficher la boîte de dialogue Publier et annoter lors de la publication** .  
  
4.  Cliquez sur **Publier**.  
  
> [!NOTE]  
>  Si vous ajoutez de nouveaux membres (lignes) dans votre feuille de calcul et vous n’arrivez pas à les publier correctement sur le référentiel MDS, il est possible que vous n’ayez pas l’autorisation **Mettre à jour** sur tous les attributs dans la feuille de calcul. Sur l'onglet **Révision** , dans le groupe **Modifications** , cliquez sur **Ôter la protection de la feuille** et réessayez de publier à nouveau.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Appliquer des règles d’entreprise &#40;Complément MDS pour Excel&#41;](apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Publication des Complément MDS pour Excel de &#40;de données&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)   
 [Validation des Complément MDS pour Excel de données &#40;&#41;](validating-data-mds-add-in-for-excel.md)  
  
  
