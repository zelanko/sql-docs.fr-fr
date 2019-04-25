---
title: Requérir des valeurs d’attribut (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c635c6083c42be3d1e3eb84afc8f188b0bdf94a5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62763838"
---
# <a name="require-attribute-values-master-data-services"></a>Requérir des valeurs d'attribut (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], requérez des valeurs d'attribut lorsque vous souhaitez vérifier que vos données de référence sont complètes.  
  
> [!NOTE]  
>  Les membres sans valeurs d'attribut basé sur un domaine ne sont pas affichés dans les hiérarchies dérivées basées sur ces relations.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-require-attribute-values"></a>Pour requérir des valeurs d'attribut  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Maintenance des règles d’entreprise** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Entité** , sélectionnez une entité.  
  
5.  Dans la liste **Type de membre** , sélectionnez un type de membre auquel appliquer la règle d’entreprise.  
  
6.  Dans la liste **Attribut** , sélectionnez un attribut ou conservez l’option par défaut **Tout**.  
  
7.  Cliquez sur **Ajouter une règle d’entreprise**.  
  
8.  Cliquez sur **Modifier la règle d’entreprise sélectionnée**.  
  
9. Dans le volet **Composants** , développez le nœud **Actions** .  
  
10. Cliquez sur **est requise** et faites-la glisser vers le **puis** du volet **Action** étiquette.  
  
11. Dans le volet **Attributs** , cliquez sur un attribut et faites-le glisser vers l’étiquette **Sélectionner un attribut** du volet **Modifier l’action** .  
  
12. Dans le volet **Modifier l’action** , cliquez sur **Enregistrer l’élément**.  
  
13. Cliquez sur **Précédent**.  
  
14. (Facultatif) Dans la page **Maintenance des règles d’entreprise** , sur la ligne qui contient votre règle d’entreprise, double-cliquez sur une cellule dans la colonne **Nom**, **Description**ou **Notification** pour mettre à jour la valeur.  
  
15. Cliquez sur **Publier les règles d’entreprise**.  
  
16. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. L’état de la règle devient **Actif**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Appliquez des règles d'entreprise aux données en suivant l'une de ces procédures :  
  
    -   [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Hiérarchies dérivées &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
