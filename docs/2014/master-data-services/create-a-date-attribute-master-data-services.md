---
title: Créer un attribut de date (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating date attributes [Master Data Services]
- attributes [Master Data Services], creating date attributes
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7362431d33af429090497e9502daf1e1730fb768
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52755424"
---
# <a name="create-a-date-attribute-master-data-services"></a>Créer un attribut de date (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez créer un attribut date lorsque vous souhaitez que les utilisateurs entrent une date comme valeur d'attribut.  
  
> [!NOTE]  
>  L'attribut est appelée DateTime, mais les valeurs d'heure ne sont pas prises en charge.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Vous devez avoir une entité pour laquelle créer l'attribut. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-create-a-date-attribute"></a>Pour créer un attribut de date  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Sélectionnez la ligne de l'entité pour laquelle vous souhaitez créer un attribut.  
  
5.  Cliquez sur **Modifier l'entité sélectionnée**.  
  
6.  Dans la page **Modifier l'entité** :  
  
    -   Si l'attribut est destiné à des membres feuille, dans le volet **Attributs de membre feuille** , cliquez sur **Ajouter un attribut feuille**.  
  
    -   Si l'attribut est destiné à des membres consolidés, dans le volet **Attributs de membre consolidé** , cliquez sur **Ajouter un attribut consolidé**.  
  
    -   Si l'attribut est destiné à des collections, dans le volet **Attributs de collection** , cliquez sur **Ajouter un attribut de collection**.  
  
7.  Dans la page **Ajouter un attribut** , sélectionnez l'option **Forme libre** .  
  
8.  Dans la zone **Nom** , tapez un nom pour l'attribut. Pour obtenir la liste des mots qui ne doivent pas être utilisés comme noms d’attributs, consultez [Mots réservés &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).  
  
9. Dans la zone **Largeur d'affichage en pixels** , tapez la largeur de la colonne d'attribut à afficher dans la grille **Explorateur** .  
  
10. Dans la liste **Type de données** , sélectionnez **DateTime**.  
  
11. Dans la liste **Masque d’entrée** , sélectionnez un format pour les dates.  
  
12. Sélectionnez éventuellement **Activer le suivi des modifications** pour effectuer le suivi des modifications apportées aux groupes d'attributs. Pour plus d’informations, consultez [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
13. Cliquez sur **Enregistrer l'attribut**.  
  
14. Dans la page **Maintenance de l'entité** , cliquez sur **Enregistrer l'entité**.  
  
## <a name="to-display-the-time-portion-of-a-datetime-value"></a>Pour afficher la partie heure d'une valeur datetime  
 Pour que l'interface utilisateur affiche la partie heure d'une valeur datetime, vous devez sélectionner un masque de saisie approprié pour l'attribut. Aucun des masques intégrés des attributs Datetime ne le permet, mais vous avez la possibilité d'ajouter un nouveau masque grâce auquel vous pourrez afficher l'heure. Pour ce faire, ajoutez une ligne dans la table mdm.tblList de la base de données MDS, dans laquelle sont stockés les masques intégrés. La ligne doit contenir les valeurs suivantes :  
  
|||  
|-|-|  
|ListCode|lstInputMask|  
|ListName|Masque d’entrée|  
|Seq|19|  
|Option de liste|jj/MM/aaaa hh:mm:ss tt|  
|ID d'option|19|  
|EstVisible|1|  
|Group_ID|3|  
  
 Une fois que vous avez entré une ligne comportant les valeurs ci-dessus dans la table mdm.tblList, le masque « jj/MMM/aaaa hh:mm:ss tt » devient disponible dans la zone de liste de masque de saisie. Vous pouvez alors sélectionner ce masque afin d'afficher la date et l'heure dans la colonne d'attribut datetime d'une entité dans l'Explorateur MDS.  
  
 Le masque de saisie est une chaîne au format DateTime .NET personnalisée. Pour plus d’informations, consultez [Chaînes de format de date et d’heure personnalisées](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [Modifier un nom d’attribut &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)   
 [Créer un attribut basé sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Créer un attribut de fichier &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
