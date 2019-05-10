---
title: Sécurité (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 56bc41ea-de28-4184-aa7e-99111ae55af5
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 80be0aea6705ed98fd12ea3481af59e289b94604
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65482585"
---
# <a name="security-master-data-services"></a>Sécurité (Master Data Services)
  Utilisez la sécurité dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]pour vous assurer que les utilisateurs ont accès aux données de référence spécifiques nécessaires pour réaliser leur travail, et les empêcher d'accéder aux données qui ne doivent pas leur être accessibles.  
  
 Vous pouvez également utiliser la sécurité pour attribuer à un utilisateur le rôle d'administrateur d'un modèle et d'une zone fonctionnelle spécifiques (par exemple, pour lui permettre de créer des versions du modèle Customer ou pour lui donner la possibilité de définir des autorisations de sécurité).  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est basée sur des utilisateurs et des groupes de domaine local ou Active Directory. La sécurité MDS vous permet d'utiliser un niveau de détail granulaire pour déterminer les données auxquelles un utilisateur peut accéder. En raison de sa granularité, la sécurité peut rapidement se compliquer et vous devez être prudent lorsque vous utilisez le chevauchement des utilisateurs et des groupes. Pour plus d’informations, consultez [Chevauchement des autorisations d’accès &#40;Master Data Services&#41;](overlapping-user-and-group-permissions-master-data-services.md).  
  
 Vous pouvez attribuer un accès de sécurité dans la zone fonctionnelle **Autorisations d'accès** de l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ou à l'aide du service Web.  
  
## <a name="types-of-users"></a>Types d'utilisateurs  
 Il existe deux types d'utilisateurs dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]:  
  
-   ceux qui accèdent aux données dans la zone fonctionnelle **Explorateur** ;  
  
-   ceux qui ont la possibilité d'effectuer des tâches d'administration dans des zones autres que la zone **Explorateur**. Ces utilisateurs sont appelés [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
## <a name="how-to-set-security"></a>Comment définir la sécurité  
 Pour accorder à un utilisateur ou un groupe l'autorisation d'accéder à des données ou des fonctionnalités dans MDS, vous devez attribuer les droits suivants :  
  
-   [Accès à la zone fonctionnelle](../../2014/master-data-services/functional-area-permissions-master-data-services.md), qui détermine laquelle des cinq zones fonctionnelles de l'interface utilisateur est accessible à l'utilisateur.  
  
-   [Autorisations d'objet de modèle](../../2014/master-data-services/model-object-permissions-master-data-services.md), qui déterminent les attributs auxquels un utilisateur peut accéder, et le type d'accès (lecture ou mise à jour) dont dispose l'utilisateur sur ces attributs.  
  
-   [Autorisations des membres de la hiérarchie](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)(le cas échéant), qui déterminent les membres auxquels un utilisateur peut accéder, et le type d'accès (lecture ou mise à jour) dont l'utilisateur dispose sur ces membres.  
  
 Lorsque vous affectez des autorisations à des attributs et des membres, ces autorisations se croisent et des règles déterminent leur ordre de priorité. Pour plus d’informations, consultez [Mode de détermination des autorisations &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md).  
  
 Pour implémenter la sécurité de niveau enregistrement, créez une hiérarchie pour une entité, puis affectez des autorisations d'utilisateur aux membres de cette hiérarchie. Les membres sont des enregistrements de données.  Les autorisations de membre de hiérarchie doivent être utilisées uniquement lorsque vous souhaitez qu'un utilisateur ait un accès limité à des membres spécifiques.  
  
 L'illustration suivante montre la hiérarchie dérivée pour l'entité de style, ainsi que les autorisations de membre de style pour un utilisateur sélectionné. Des autorisations de mise à jour sont attribuées aux membres M {Men's} et U {Unisex}, et des autorisations en lecture seule sont attribuées au membre Women's Style. Cela signifie que l'utilisateur peut mettre à jour les enregistrements correspondant aux produits Men's et Unisex, et uniquement lire les enregistrements correspondant aux produits Women's Style.  
  
 ![Style de la hiérarchie dérivée et membre autorisations](../../2014/master-data-services/media/style-derived-hierarchy-mds.png "autorisations de membre et le Style de la hiérarchie dérivée")  
  
 Pour plus d’informations sur la création d’une hiérarchie, consultez [créer une hiérarchie explicite &#40;Master Data Services&#41; ](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) et [créer une hiérarchie dérivée &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md).  
  
 Pour plus d’informations sur la façon d’affecter des autorisations de membres, consultez [affecter des autorisations des membres de hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## <a name="security-in-the-add-in-for-excel"></a>Sécurité du complément pour Excel  
 La sécurité définie dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] s'applique également à [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]. Les utilisateurs peuvent uniquement afficher et utiliser les données pour lesquelles ils ont l'autorisation nécessaire. Les administrateurs peuvent effectuer les tâches d'administration.  
  
 La seule mise en garde est que toute la sécurité affectée dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ne s'applique pas à Excel tant qu'un intervalle de 20 minutes ne s'est pas écoulé. L'intervalle est défini par le paramètre *MdsMaximumUserInformationCacheInterval* du fichier web.config. Pour modifier l'intervalle, vous pouvez modifier le paramètre et redémarrer IIS.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créer un utilisateur disposant d'une autorisation totale sur un modèle.|[Créer un administrateur de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)|  
|Ajouter un groupe Active Directory à [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]; il s'agit de la première étape pour accorder à un groupe l'autorisation d'accéder aux données dans l'application Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|[Ajouter un groupe &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-group-master-data-services.md)|  
|Accorder une autorisation d'accès à une zone fonctionnelle de l'application Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|[Affecter des autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../../2014/master-data-services/assign-functional-area-permissions-master-data-services.md)|  
|Accorder une autorisation d'accès aux valeurs d'attribut en accordant une autorisation d'accès aux objets de modèle.|[Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)|  
|Accorder une autorisation d'accès aux valeurs de membre en accordant une autorisation d'accès aux nœuds de la hiérarchie.|[Affecter des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)   
 [Utilisateurs et groupes &#40;Master Data Services&#41;](../../2014/master-data-services/users-and-groups-master-data-services.md)   
 [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Autorisations des membres de la hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Mode de détermination des autorisations &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
