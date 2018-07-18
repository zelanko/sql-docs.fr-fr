---
title: Changer le type d’attribut (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c1e087cb853e6517c0977b2db33c31312631c1ca
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37195429"
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a>Modifier le type d'attribut (complément MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], les administrateurs peuvent modifier le type d’attribut lorsque le type de données ou le nombre de caractères autorisé est incorrect.  
  
 Si vous souhaitez modifier le type d’attribut pour créer une liste contrainte (attribut basé sur un domaine), consultez [Créer un attribut basé sur un domaine &#40;Complément MDS pour Exce&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas mettre à jour le type ou la longueur des colonnes **Nom** ou **Code**.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder aux zones fonctionnelles **Administration de système** et **Explorateur** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).  
  
-   Un modèle, une entité et un attribut doivent exister.  
  
### <a name="to-change-the-attribute-type"></a>Pour modifier le type d'attribut  
  
1.  Dans Excel, chargez l'entité qui contient la colonne (attribut) que vous souhaitez modifier. Pour plus d’informations, consultez [charger des données à partir de MDS dans Excel](export-data-to-excel-from-master-data-services.md).  
  
2.  Cliquez sur une cellule de la colonne que vous souhaitez modifier.  
  
3.  Dans le groupe **Modèle de build** , cliquez sur **Propriétés d'attribut**.  
  
4.  Dans la boîte de dialogue **Propriétés d'attribut** , mettez à jour les paramètres si nécessaire.  
  
5.  Cliquez sur **OK**.  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a>Que se passe-t-il lorsque vous modifiez le type d'attribut ?  
 S'il existe une dépendance sur l'attribut, par exemple si l'attribut est référencé par une règle d'entreprise MDS ou si l'attribut est inclus dans une vue d'abonnement, et si vous modifiez le type de données d'un attribut, MDS va :  
  
-   Modifier le type de données de l'attribut.  
  
-   Générer une copie de l'attribut avec le suffixe « _old » qui ne contient aucune valeur. Il s’agit une **déconseillée** attribut.  
  
 Cependant, toutes les dépendances existantes sur l'attribut d'origine pointeront vers l'attribut déconseillé, et non vers celui modifié.  
  
 Cela implique que :  
  
-   Vous devez actualiser les règles d'entreprise pour indiquer l'attribut modifié car la logique peut ne pas être la même avec le nouveau type de données de l'attribut. Vous devrez modifier chaque règle affectée, puis retravailler les expressions pour supprimer les références de l'attribut déconseillé (_old) et utiliser l'attribut mis à jour.  
  
-   Vous devez ouvrir les vues d’abonnement dans la sélection de la gestion de l’intégration, sélectionnez la ligne de vue, ouvrir pour le modifier en cliquant sur l’icône de crayon, puis cliquez sur le **enregistrer disque** icône pour actualiser la définition de vue. Aucune autre modification n'est nécessaire pour régénérer la syntaxe de la vue.  
  
-   Les tables intermédiaires qui incluent l'attribut comprendront une colonne d'attribut déconseillé, ce qui signifie que votre code intermédiaire sera affecté. Pour vous débarrasser de l'attribut déconseillé, vous pouvez le supprimer après avoir mis à jour les règles d'entreprise et les vues d'abonnement.  
  
 **Suppression de l’attribut déconseillé**  
  
 Avant de supprimer un attribut déconseillé, vous devez supprimer toutes les références à l'attribut, par exemple, en corrigeant les règles d'entreprise et en régénérant les vues d'abonnement comme décrit plus haut. Sinon, vous obtiendrez une erreur dans la page Web Administration de système lorsque vous tenterez de supprimer l'attribut déconseillé, indiquant que l'attribut ne peut pas être supprimé car il est référencé par un objet.  
  
 Pour supprimer un attribut, consultez [supprimer un attribut &#40;Master Data Services&#41;](../delete-an-attribute-master-data-services.md)  
  
> [!TIP]  
>  Modifier les types de données des attributs MDS qui incluent des données existantes et des entités associées est une opération lourde, notamment s'il existe une règle d'entreprise ou une vue d'abonnement déclarée qui dépend de l'entité. La méthode recommandée est de commencer à utiliser un type de données qui est suffisamment flexible pour contenir les valeurs requises. Par exemple, les chaînes sont souvent courtes au début, mais il peut être nécessaire de les rallonger au fil du temps ; par conséquent, considérez le pire des scénarios. Les chaînes de texte longues peuvent être fastidieuses à gérer (par exemple, il est difficile d'ajuster à l'écran des zones de texte longues dans l'interface utilisateur graphique) ; par conséquent, évitez les chaînes trop longues.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs &#40;Master Data Services&#41;](../attributes-master-data-services.md)   
 [Génération d’un modèle &#40;Complément MDS pour Excel&#41;](building-a-model-mds-add-in-for-excel.md)  
  
  
