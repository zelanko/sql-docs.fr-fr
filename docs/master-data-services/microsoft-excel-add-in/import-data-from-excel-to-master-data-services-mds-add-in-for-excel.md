---
title: "Publier des données d’Excel dans Master Data Services (Complément MDS pour Excel) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
caps.latest.revision: 10
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 3051e6d5cbeef00ce4b05ee03bc39e79271207be
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="import-data-from-excel-to-master-data-services-mds-add-in-for-excel"></a>Publier des données d’Excel dans MDS (Complément MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous pouvez publier les données dans le référentiel MDS quand vous avez fini de travailler dans Excel et souhaitez enregistrer vos modifications afin que d’autres utilisateurs puissent y accéder.  
  
> [!NOTE]  
>  -   Lorsque vous publiez des modifications, les commentaires sur les cellules managées MDS sont supprimés.  
> -   Une formule n'est pas prise en charge dans une cellule managée MDS. Une formule dans une cellule managée MDS est traitée comme valeur de texte.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   La feuille de calcul active doit contenir des données managées MDS et vous devez avoir apporté des modifications ou effectué des ajouts à ces données.  
  
-   Si vous ajoutez des membres, vous ne devez pas spécifier de valeur **Code** si les codes de l'entité sont générés automatiquement. Pour plus d’informations, consultez [Création automatique de code &#40;Master Data Services&#41;](../../master-data-services/automatic-code-creation-master-data-services.md).  
  
### <a name="to-publish-data-to-the-mds-repository"></a>Pour publier des données dans le référentiel MDS  
  
1.  Dans le groupe **Publier et valider** , cliquez sur **Publier**.  
  
2.  Ce paramètre est facultatif. Si la boîte de dialogue **Publier et annoter** s’affiche, choisissez de partager la même annotation (commentaire) pour toutes les mises à jour, ou d’annoter chaque modification individuellement.  
  
3.  Ce paramètre est facultatif. Activez la case à cocher **Ne plus afficher cette boîte de dialogue** . Vous pouvez toujours afficher la boîte de dialogue ultérieurement en choisissant **Paramètres** et en sélectionnant la case à cocher **Afficher la boîte de dialogue Publier et annoter lors de la publication** .  
  
4.  Cliquez sur **Publier**.  
  
> [!NOTE]  
>  Si vous ajoutez de nouveaux membres (lignes) dans votre feuille de calcul et vous n’arrivez pas à les publier correctement sur le référentiel MDS, il est possible que vous n’ayez pas l’autorisation **Mettre à jour** sur tous les attributs dans la feuille de calcul. Sur l'onglet **Révision** , dans le groupe **Modifications** , cliquez sur **Ôter la protection de la feuille** et réessayez de publier à nouveau.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Appliquer des règles d’entreprise &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : importation de données à partir d’Excel &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)   
 [Validation des données &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md)  
  
  

